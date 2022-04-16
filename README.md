# YouTube-Unsubscribe-Script

If you have used the same YouTube account for years, you probably subscribed to many channels. This scenario makes it easier to follow uploads from your favorite content creators, but it has its downsides. In case you clicked on the option to get bell notifications for every single upload from every YouTuber you subscribed to, you have to deal with a ton of notifications.
![How-to-Do-a-Mass-Unsubscribe-in-YouTube](https://user-images.githubusercontent.com/28998081/163663771-6255e240-2066-4eff-8a05-606287835352.jpg)
Unfortunately, YouTube does not have a native option to mass unsubscribe from channels because it does not want you to do it. On the bright side, you can do it yourself, and we are going to show you how.
Unsubscribe from YouTube Channels One at a Time

If you have lost interest in a YouTube channel, there are several ways to unsubscribe.

    Clicking on one of the channel’s videos and clicking the gray “Subscribe” button to unsubscribe.
    Clicking on the channel’s homepage and doing the same process as above.
    Going to your Subscriptions page, choosing “Manage,” and unsubscribing to the listing.
    Heading to your “Manage” page and running a script to bulk delete all subscriptions.

You probably already know how to unsubscribe YouTube channels one by one, and know that it is very time-consuming. But, did you know you can go to the YouTube subscription manager and see all the channels you are subscribed to?

View Your Existing YouTube Subscriptions List by doing the following:

    Log in to your YouTube account.
    Click on Subscriptions.
    Click on “Manage” in the top-right corner.

You can now scroll through all of your subscriptions here and decide which ones you want to keep watching and which ones you want to get rid of. This method is excellent for YouTube users who are selective about their subscriptions and don’t want to lose all of them.

Because of the confirmation pop-ups, the manual unsubscribe process still requires many clicks depending on the number of channels that you follow. If you want a better solution, try the methods below.
Mass Unsubscribe from All YouTube Channels

The following method allows you to mass-unsubscribe from all the YouTube Channels you follow. Remember that you will need to subscribe again to the ones you still enjoy. It might be a good idea to write down their names and URLs, so you don’t forget about them.

Bulk unsubscribing from YouTube requires you to run a script, but don’t worry, this method was tried, tested, and verified. Plus, you don’t need to install any potentially harmful third-party program on your computer.

Follow these steps to mass unsubscribe:

  1. Go to your subscription manager by clicking on “Subscriptions.
![You-Tube-mass-unsubscribe-1](https://user-images.githubusercontent.com/28998081/163663819-e6838350-7a34-4264-beda-d200ee701cfc.jpg)

  2. Click on “Manage” in the upper-right section.
![You-Tube-mass-unsubscribe-2](https://user-images.githubusercontent.com/28998081/163663935-c7698816-b044-4438-803c-62da4592cfcb.jpg)

  3. Scroll down to the “bottom” of your subscriptions or find an empty spot on the page. Right-click the empty area (shows cursor, not hand) and select the “Inspect Element” or “Inspect” option.
![You-Tube-mass-unsubscribe-3](https://user-images.githubusercontent.com/28998081/163663944-d6df8a13-686b-4505-a6f0-82534b40b6ef.jpg)

  4. Click on the Console tab, which is the second tab at the top.
![You-Tube-mass-unsubscribe-4](https://user-images.githubusercontent.com/28998081/163663956-b88c485f-1299-44c9-aedf-ed7bb86da6c9.jpg)

  5. Scroll to the bottom of the console until you reach the “>” symbol.
![You-Tube-mass-unsubscribe-5](https://user-images.githubusercontent.com/28998081/163663968-fc4720ca-bd6a-485d-a826-ce2065431fa2.jpg)

  6. Copy the code below into the command field and press “Enter.” The Console should look like this while pasting the entire script:
![YouTube-mass-unsubscribe-6](https://user-images.githubusercontent.com/28998081/163663974-c9a570a6-a6c0-449f-a309-2aad91810602.jpg)
/** 
  * Youtube bulk unsubsribe fn.
 * Wrapping this in an IIFE for browser compatibility.
  */
(async function iife() {
   // This is the time delay after which the "unsubscribe" button is "clicked"; Tweak to your liking!
  var UNSUBSCRIBE_DELAY_TIME = 2000
 
/**
  * Delay runner. Wraps `setTimeout` so it can be `await`ed on. 
 * @param {Function} fn 
  * @param {number} delay 
 */
   var runAfterDelay = (fn, delay) => new Promise((resolve, reject) => {
    setTimeout(() => {
       fn()
      resolve()
     }, delay)
  })
 

 
  // Get the channel list; this can be considered a row in the page.
   var channels = Array.from(document.getElementsByTagName(`ytd-channel-renderer`))
  console.log(`${channels.length} channels found.`)
 
  var ctr = 0
   for (const channel of channels) {
    // Get the subsribe button and trigger a "click"
     channel.querySelector(`[aria-label^='Unsubscribe from']`).click()
    await runAfterDelay(() => {
       // Get the dialog container...
      document.getElementsByTagName(`yt-confirm-dialog-renderer`)[0]
         // and find the confirm button...
        .querySelector(`#confirm-button`)
         // and "trigger" the click!
        .click()
       console.log(`Unsubsribed ${ctr + 1}/${channels.length}`)
      ctr++
     }, UNSUBSCRIBE_DELAY_TIME)
  }
 })()

Watch as your subscriptions disappear, one by one.
![YouTube-mass-unsubscribe-100](https://user-images.githubusercontent.com/28998081/163663991-8d826eca-c6d9-495c-ae7c-6210b912e69c.png)

Don’t panic if progress slows down or appears frozen in time. The script causes that status while it works its magic. You can copy/paste the code into the Console and rerun it if you don’t get rid of all subscriptions on the first try.

Be sure to refresh the page before you rerun the script! You should also refresh the page to confirm all subscriptions are gone. When you go back to the “Subscribe” page, the “Manage” option in the top-right section will no longer be there because, after all, you have no more subscriptions.
    
