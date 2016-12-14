---
title: AppStore Icon Quest
categories:
- Long
tags:
- Code
- Automation
- Icons
- iOS
- OSX
---

[Skip to the prize](https://matt-mccabe-fkn5.squarespace.com/config#script) if you don't care how I did it.

#In the beginning...


Brett Terpstra wrote about how to 
[Instantly grab a high-res icon for any iOS app](http://brettterpstra.com/2013/04/28/instantly-grab-a-high-res-icon-for-any-ios-app/) and I started it using the automator application straight away for a project1 I'm working on.

It's really hard to find consistently sized iOS icons, I really wanted the 
Omnifocus for iPhone icon but it just wasn't being returned in the search, it kept returning the iPad icon.

##I won't be defeated that easily!


I tried many searches and went through pages of icons but couldn't find anything above 512x512, unacceptable!

Then I got my breadcrumb, I spotted a comment on Brett's post mentioning that if I change 
iPadSoftware for 
macSoftware it would be possible to find the Mac version of the icon. So how could I find the bloody iPhone icon? Simple really, I switched 
iPadsoftware for 
software! Thanks 
[StackOverflow](http://stackoverflow.com/questions/6848650/itunes-search-api-is-there-a-way-to-get-all-apps-iphone-ipad-mac-for-a-ce) for that piece of the jigsaw.

After working out how to amend the search I finally got the result I wanted, a nice 1024x1024 Omnifocus for iPhone icon but I was on a roll. What if I wanted to do that again, How could I improve the experience? wouldn't it be nice to have a menu to choose what type of icon to search for? Of course it would!

##Down the ruby encrusted apple-hole I go


I knew what I wanted to do, the next question was how. I'd never written a line of Ruby and had only created the most basic Automator applications to batch rename some files.

I thought changing the Ruby script would be the hardest part, it wasn't too bad. From the start I had the idea to pass something like 1|Omnifocus to the Ruby script, use the prefix to determine the software to search for and the remainder would be the search term.

After working out the syntax for a case statement I dropped that in like so:

case terms[0..0]when "1"; storeselected="software"when "2"; storeselected="iPadSoftware"when "3"; storeselected="software,iPadSoftware"when "4"; storeselected="macSoftware" end

Next I needed someway of splitting the string in two. Usually I'd use a left or mid or substr function but Ruby was little different to what I'm used to, don't ask me to explain it:

terms[2..-1]

So that gave me the search term, then for some reason I thought I should use RegEx - I'd never used it before, I think Merlin Mann must have mentioned it on Back to Work - to check if a prefix had been chosen. I used the fantastic 
[Rubular](http://rubular.com/) to create this little gem:

/\A\d[|]{1}/

This matched the first number plus the pipe (|) which I could then use this with my case statement. This meant if the user missed out the prefix it will just search all types.

##Bring out the Automator!


So far so good, but my method of input still relies on the prefix being typed in. Not good.

I needed a menu, the 'choose from list' combined with 'filter paragraphs' was supposed to do this but I couldn't get it working the way I wanted. So I had to break out the AppleScript.

The idea was to present a friendly menu like this

*1| iPhone


*2| iPad


*3| iOS


*4| Mac

I had to rely on some fine searching to get what I needed and even then I found the syntax and data types pretty frustrating. What I would normally do in one line of code took three.

set SubString to result as stringset SubString to text 1 thru 2 of SubStringreturn SubString as string

So what I'd done was substring the result to get the prefix, e.g. 1| and pass it to the next action. I also made sure if the user pressed cancel it would quit instead of going to the next action. So the first Applescript was set:

on run local SubString set result to (choose from list {"1| iPhone", "2| iPad", "3| iOS", "4| Mac"} with prompt "Please select the type of icon you'd like to search for" without multiple selections allowed and empty selection allowed) if result is false then quit else set SubString to result as string set SubString to text 1 thru 2 of SubString return SubString as string end ifend run

This ended up simplifying the ruby script and killing my nice little RegEx :(

##Invisibility? You stole that from Lord of the Rings!


Next up was the dialog box, initially I used the action 'Ask for Text' which took the text select from the menu and put it input box of the Application Name form. This mean the text was selected so as soon as you typed it dissapeared, unless you press or click to the right of the text. I forgot to do that everytime. Unacceptable!

So I had to find a way of invisibly passing the parameter. Back to Applescript.

As you can see the Applescript takes input which is the prefix from the menu. Instead of displaying it, it just concatenates it with the text that user types into the dialog box. Nice little trick and no Nazgûl to be seen, suck on that Frodo.

on run {input, parameters} set prefix to input as string set term to the text returned of (display dialog "Application name, be as specific as possible" default answer "" buttons {"OK"} default button 1) return prefix & termend run

As this Automator application only has 2 actions it doesn't require too much parsing in the script but in theory you could chain multiple menus and dialogs and process it with the script.

##Ruby, ruby, ruby, ruby you haven't change much


I've only really added a few lines of code to this section to select the right search type and search term.

#!/usr/bin/ruby# encoding: utf-8## Original script created by Brett Terpstra # Source: http://brettterpstra.com/2013/04/28/instantly-grab-a-high-res-icon-for-any-ios-app/## Modified by Matt McCabe to include selection of icon type# Source: http://mattmadethis.com/where-it-is-located.html## Retrieve an AppStore (iPhone, iPad, iOS or Mac) app icon at the highest available resolution# All arguments are combined to create an iTunes search# The icon for the first result, if found, is written to a filename based on search terms## example:# $ ipadicon super monsters ate my condo %w[net/http open-uri cgi].each do |filename| require filenameenddef find_icon(terms) case terms[0..0]when "1"; storeselected="software"when "2"; storeselected="iPadSoftware"when "3"; storeselected="software,iPadSoftware"when "4"; storeselected="macSoftware" endurl = URI.parse("http://itunes.apple.com/search?term=#{CGI.escape(terms[2..-1])}&entity=#{storeselected}") res = Net::HTTP.get_response(url).body match = res.match(/"artworkUrl512":"(.*?)",/) unless match.nil?return match[1] else return false endend terms = ARGV.join(" ")icon_url = find_icon(terms)unless icon_url puts "Error: failed to locate iTunes url. You may need to adjust your search terms." exitendurl = URI.parse(icon_url)target = File.expand_path("~/Desktop/"+terms.gsub(/[^a-z0-9]+/i,'-')+"."+icon_url.match(/\.(jpg|png)$/)[1])begin open(url) do |f|File.open(target,'w+') do |file| file.puts f.readendputs "Icon saved to #{target}." endrescue puts "Error: failed to save icon."end

##[Quest Over, collect your prize]()


Download the (zipped) 
[AppStoreIcon.app](http://static.squarespace.com/static/52001c0be4b09bc7c9f838c9/52001dc8e4b05c9447cc624e/52001dcbe4b05c9447cc630d/1369251128000/AppStoreIcon.app_.zip?format=original) and give it a try. Thanks again to 
[Brett Terpstra](http://brettterpstra.com/) for getting me start and a few tips along the way.

Take a look at 
[this little clarify guide](http://mttmccb.clarify-it.com/d/v9nywj) if you're struggling to understand how it works. Ok so it's really easy I just wanted to try out 
[clarify](http://www.clarify-it.com/), it really easy to use.

I'm sure this could be improved, for example I'd like to do a version that adds the transparent mask using ImageMagick, maybe next time. Here are the unmasked icons side by side, see there is a difference, slightly... :D 
![Omnifocus-for-iPad](/squarespace_images/static_52001c0be4b09bc7c9f838c9_52224ed3e4b0ba9919a3e0e1_52001dcbe4b05c9447cc6313_1375739348283_Omnifocus-for-iPad.png_) Omnifocus-for-iPad 
![Omnifocus-for-iPhone](/squarespace_images/static_52001c0be4b09bc7c9f838c9_52224ed3e4b0ba9919a3e0e1_52001dcbe4b05c9447cc6310_1375739351114_Omnifocus-for-iPhone.png_) Omnifocus-for-iPhone 
1. I need some nice icons and got a little side tracked...
