### What is it?

It's a project that allows you fix a long standing bug in bunq's mobile app using [Postman](https://www.getpostman.com).

**A bug you say?**

Yeah, unfortunately I've experienced a bug for a while. Not a very serious bug, but bad enough to lead to frustration. I didn't receive any notifications of the support chat messages.

In other words, every time I had a conversation with support I had to check every once in a while if I already had a response. Instead of being able to wait until I got a notification. Even after repeatedly setting my notification settings via the app, the problem continued to occur. Until I realized that I could also change my notification settings via the bunq API.

I compared the list of push notification filters with a user who had the support notifications working. And yes, I missed a filter, the `SUPPORT` filter.

With this collection of postman API requests you can easily add the support filter back to the list of your notification filters.

**Note:** As soon as you change the notification settings via the app, this change will be undone. As this doesn't address the bug at its roots, but it only fixes the symptom.

### How does one use it?

1. [Get Postman](https://www.getpostman.com/apps)
2. Run it. Don't bother signing in if you don't want to, there's a small link on the bottom to skip. This project does
   not use any of Postman's cloud features.
3. Click `Import` button in top left and drag all the files from the project there
4. In top right corner select your environment (sandbox or production).
5. If you selected production, edit the environment using the "eye" icon. Set "current value" of `api_key` to your API 
   key.
6. Run `Create an installation`, `Add the device`, `Add a session` in that order. They will create everything needed for
   using public API, including RSA keys, session and installation tokens. For you reference all those values will be set
   in the environment.
7. Run `Get push notification filters` to receive a list with you current push notification filters. You'll need this for the next step
8. Take a look at the body of the `Update notification filters` request. Here you'll find an almost empty list of notification filters, only the `SUPPORT` filter is listed. Add all the filters from the previous step to this list and run the request. (See below for a sample with all notification filters active.)
9. You're done, you should now have working push notifications for support! 

### I don't know how JSON works...
#### Just give me the whole list with filters that I can past into step 8.

```JSON
{
	"notification_filters": [
		{
			"category": "SUPPORT"
		},
		{
			"category": "SLICE_REGISTRY_MEMBERSHIP"
		},
		{
			"category": "SLICE_REGISTRY_SETTLEMENT"
		},
		{
			"category": "SLICE_REGISTRY_ENTRY"
		},
		{
			"category": "ACHIEVEMENT"
		},
		{
			"category": "BILLING"
		},
		{
			"category": "FLARUM"
		},
		{
			"category": "CARD"
		},
		{
			"category": "CARD_TRANSACTION_SUCCESSFUL"
		},
		{
			"category": "CARD_TRANSACTION_FAILED"
		},
		{
			"category": "CARD_TRANSACTION_UPDATED"
		},
		{
			"category": "REQUEST"
		},
		{
			"category": "REMINDER_REQUEST"
		},
		{
			"category": "TAB_RESULT"
		},
		{
			"category": "WHITELIST"
		},
		{
			"category": "WHITELIST_RESULT"
		},
		{
			"category": "PAYMENT"
		},
		{
			"category": "INSTANT_PAYMENT"
		},
		{
			"category": "BUNQME_TAB"
		},
		{
			"category": "IDEAL"
		},
		{
			"category": "SCHEDULE_STATUS"
		},
		{
			"category": "SCHEDULE_RESULT"
		},
		{
			"category": "DRAFT_PAYMENT"
		},
		{
			"category": "REWARD"
		},
		{
			"category": "SOFORT"
		},
		{
			"category": "BANK_SWITCH_SERVICE_PAYMENT"
		},
		{
			"category": "BUNQME_FUNDRAISER"
		},
		{
			"category": "INTEREST"
		},
		{
			"category": "CHECKOUT_MERCHANT"
		},
		{
			"category": "BARZAHLEN"
		},
		{
			"category": "SUPPORT"
		},
		{
			"category": "LOCATION_EVENT"
		}
	]
}
```
