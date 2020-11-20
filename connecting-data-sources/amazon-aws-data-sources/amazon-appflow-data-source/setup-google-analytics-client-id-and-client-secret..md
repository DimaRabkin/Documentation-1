# Setup Google Analytics client ID and client secret.



1. On the Google API Console \([https://console.developers.google.com](https://console.developers.google.com/)\), choose **Library**.
2. Enter `analytics` in the search field.
3. Choose **Google Analytics API**.
4. Choose **ENABLE** and return to the previous page.
5. Choose **Google Analytics Reporting API** listed in the search results.
6. Choose **ENABLE** and return to the main page.
7. Choose **OAuth consent screen**.
8. Create a new **Internal** app \(if you’re using your personal account, choose **External**\).
9. Choose **Add scope**.
10. Add **../auth/analytics.readonly** as **Scopes for Google APIs**.
11. Choose **Save**.
12. Choose **Credentials**.
13. Add **OAuth client ID credentials**.
14. Choose **Web application**.
15. Enter `https://console.aws.amazon.com/` as an authorized JavaScript origins URL.
16. Enter `https://`_`AWSREGION`_`.console.aws.amazon.com/appflow/oauth` as an authorized redirect URL. \(Replace _`AWSREGION`_ with the Region you’re working in. If you’re using Amazon AppFlow in `us-east-1`, enter `https://console.aws.amazon.com/appflow/oauth`.\)
17. Choose **Save**.

