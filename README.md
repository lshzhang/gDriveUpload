# How to make it work for you
Instructions modified from https://github.com/CharlesPlucker/drive-multi-upload/ (unfortunately I could not make it work using Charles Plucker's script)  
This form is made up of two files: form.html, and Code.gs. Follow these steps to run them:  

1. Go to http://script.google.com (you need to login to one and only one google account; use Incognito Window, login first before visiting script)
2. Click on "New project" at the top left of the page
3. Paste the contents of Code.gs into the Code.gs file that opens up (remove everything already in there). Modify the folder name in the first line of code:
```
mainFolderName = "my folder name";
```
4. Click at the + sign to the right of "File" then click "HTML" and name it form.html 
5. Copy the contents of form.html into the newly created form.html (remove the template already in there)
6. Deploy your code by going to "Deploy" -> "New deployment" -> "Select type" click the cockwheel, choose "Webapp"
7. On the right side "Configuration", Give a description for the App, choose "Anyone" for "Who has access", click "Deploy"
8. Authorize the app by Reviewing Permissions and allowing this script to modify your google drive. (If you see a "BACK TO SAFETY" button you should click "Advanced", then the link that says "unsafe")
9. The Webapp will show "Deployment ID", "Web app", "URL". Copy that URL link, or click to view the form. (you can always find this link again by going to "Deploy" -> "Manage deployment")

# The following contents are from original Michael Kofron copy:
https://github.com/michaelkofron/DriveRequest

# Example

https://user-images.githubusercontent.com/53279060/227257682-b6f5dd62-ce68-4fe2-9fff-13a72c614efc.mp4

# What it does
I was recently asked by a friend if I knew of a way to receive files from multiple people with a few constraints:

1. The uploader(s) shouldn't be able to see the contents of the folder
2. The uploader(s) shouldn't have to login or create an account with any service
3. The uploader(s) should be able to upload multiple files at once
4. The uploader(s) should be able to upload to the same folder multiple times by using their name and email as identifiers
5. The uploads should be categorized into folders by name and email
6. This should be done for free

"File requests" is the common term for this feature, so I started searching the internet for a service that offers free file requests that also satisfies these constraints. I couldn't find any services that were able to do this, but I did find mentions of Google Apps Script being able to provide a way to interact with a Google Drive account. Google Drive offers 15gb of storage absolutely free, and their storage tiers are reasonably priced. I found some code online that was able to achieve this somewhat, but it was littered with links to non-free services, and was intentionally limited to single file uploads of 2MB or less, rendering it pretty much useless. 

Google Apps Script is just JavaScript, so I read the docs, found [this helpful gist](https://gist.github.com/tanaikech/88fcae255abb4aac5bec81ad5ca213ef), and was able to come up with a multi-file solution that works good enough for my friend's use-case. I tried to keep the UI as simple ass possible so you can customize it to your liking. 

# Limitations

+ The upload limits are not very clear. I've uploaded up to 200MB between 100 pictures successfully from my phone in two back-to-back submission but YMMV. In my experience it capped out at 200MB+ in one submission so I set the code to limit submissions that are above 100MB just to be safe. Either way, 100MB transfer is pretty good for absolutely free. You can change the limit and test it yourself but I plan on finding the true limits soon.
+ Some people may have issues with this script if they are signed into multiple Google accounts in their browser. [This is a known issue that has still not been fixed](https://issuetracker.google.com/issues/69270374?pli=1). An easy workaround is to simply use an incognito window, or to [embed the script inside of an iframe on a different domain](https://developers.google.com/apps-script/reference/html/html-output#setXFrameOptionsMode(XFrameOptionsMode)).
+ I haven't yet tested it with multiple submissions from various devices within a short time frame, only multiple submissions back-to-back between my phone and laptop. Again, I will work on finding the true limit soon.
