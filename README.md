# Google Scholar citations API for Markdown

This repo contains a simple API that can be used within Markdown readme.md file.

Below shows `Albert Einstein`'s google scholar citation summary using this API.

![Albert Einstein Citation History](https://vercel-citations.vercel.app/api/simple?id=qc6CJjYAAAAJ)

To implement this, I wrote a custom web API that uses [serpapi](https://serpapi.com/google-scholar-api) to obtain scholar information and parsed it using a simple python script hosted on [vercel](https://vercel.com/). A `query` is google scholar ID and it will `response` with an image (shown above). 

If you want to use this in your project. You can try as below.

Change the {YOUR_Google_Scholar_ID} value to your Google Scholar ID.

```
![Your Citation History](https://vercel-citations.vercel.app/api/simple?id={YOUR_Google_Scholar_ID})
```
or
```
<p align="left"> <img src="https://vercel-citations.vercel.app/api/simple?id={YOUR_Google_Scholar_ID}" alt="Citation History" width="600"/> </p>
```
* How can I obtain my google scholar ID?

Albert Einstein's google scholar page is `https://scholar.google.com.au/citations?user=qc6CJjYAAAAJ&hl=en` and the ID is `qc6CJjYAAAAJ` (that is in between `=` and `&`).

### Notes
* Please noet that this service is hosted under free version of [serpapi](https://serpapi.com/google-scholar-api) that only allows up to 1_00 queries/month, therefore the API call may not work as expected if it exceeds the daily limit.
* In order to address API rate limit issue, a simple yet powerful feature added; hashing citation data and will be stored for 5 days. This means that your citation data will be fetched once and updated if it is not exist in a database, or exceeded 5 days. After the request, no [serpapi](https://serpapi.com/google-scholar-api) call will be requested within this 5 days period, but cached data will be used for generating citation plot instead. 5 days period is set from rough estimation of google scholar's update frequency. Simple math to estimate how many user can be hosted: Because each user's data is cached for 5 days, a single user would require 1 API query every 5 days at maximum. So a single user would need 6 API queries per month (30 / 5). Max users that this api can host will be Total Queries per Month / Queries per User per Month = 100/6 ≈ 16.67 :(

* If image can't be visualised properly, refresh it and your browser will cache it.
* The hosting script is difficult to be shared since it contains private API keys, but it is quite straight forward to realise it with `requests` and `vercel`.
* `Matplotlib` is used for plotting and only this style is supported (maybe further update if necessary)

Hope this useful somehow...
