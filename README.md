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
* Please noet that this service is hosted under free version of [serpapi](https://serpapi.com/google-scholar-api) that only allows up to 1_000 queries/day, therefore the API call may not work as expected if it exceeds the daily limit.
* If image can't be visualised properly, refresh it and your browser will cache it.
* The hosting script is difficult to be shared since it contains private API keys, but it is quite straight forward to realise it with `requests` and `vercel`.
* `Matplotlib` is used for plotting and only this style is supported (maybe further update if necessary)

Hope this useful somehow...