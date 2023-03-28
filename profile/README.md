## 🌟 1 - What is Envoy ? 

### 🌊 The Envoy flow
We help you (content apps) use your content to attract qualified leads. We do this by placing content previews inside a high-converting web flow we host on your behalf. 

<figure class="">
    <img src="https://github.com/Envoy-Technology/.github/blob/main/images/player_views_1.png?raw=true" style=""/>
</figure>

### 📣 Features
There are two key ways for you to use the Envoy flow, through **gifting** and **marketing** links:

| Feature     | Short description |      Integration needed?        | Illustrated example |
| ----------- | ----------------- | ------------------------------- | ------------------  |
| Gifting      |   Enable your users to share with their friends.   |   Yes, an API call to get gift link + a gift button on the front-end    | <img src="../images/feature_gifting.png" style="width: 400px;"/>       |
| Marketing links   | Generate links to be shared on social media or email campaigns   |    No, gets done from dash in a no-code way    | <img src="../images/feature_marketing_1.png" style="width: 400px;"/>       |
| Rewards   | Boost sharing by creating incentives for your users   |    It depends on implementation (ie rewarding signups means integrating our pixel)   | <img src="../images/feature_rewards.png" style="width: 400px;"/>       |
| Analytics   | Generate links in a no-code way                     |    No integration needed | <img src="../images/feature_analytics_1.png" style="width: 400px;"/>       |

### 🎥 🎧 Supported formats 
| Video | Audio | Live audio and video | Articles |
| --- | --- | --- | --- |
| <img src="https://github.com/Envoy-Technology/.github/blob/main/images/format_video_1.png?raw=true" style="width: 400px;"/> | <img src="https://github.com/Envoy-Technology/.github/blob/main/images/format_audio.png?raw=true" style="width: 400px;"/> | <img src=".https://github.com/Envoy-Technology/.github/blob/main/images/format_live.png?raw=true" style="width: 400px;"/> | <img src="https://github.com/Envoy-Technology/.github/blob/main/images/format_article.png?raw=true" style="width: 400px;"/> |

## 🛠️ 2 - How do I integrate Gifting into my app?

### 🔄 Step 1/2: The API call
After you've set up your space in the Envoy dash, here's the API call you'll need to make to get a link (example in Python). Read our [Tech docs](https://openapi.envoy.is/) for the full code snippets.

``` 
payload = {
    'userId': '100',
    'contentConfig': {
        'contentType': 'VIDEO',
        'contentId': '12345',
        'contentName': 'Video title',
        'contentDescription': 'A short description of the video',
        "common": {
            "media": {
                "poster": "https://your-poster-uri.com",
                "source": "https://file_link.mp3"
            }
        },
    }
}
```

The respond payload will contain a `url` and a `userRemainingQuota`. Link format is:  `[your_app_name].envoy.gift/12345`. 

### 👀 Step 2/2: Displaying that link to the user
All that's now left is to build the UI needed to show the Envoy link to the user. In an app, the simples version possible is a share link that returns the native sharing modal:

<img src="https://github.com/Envoy-Technology/.github/blob/main/images/share_modal_1.png?raw=true" style="width: 300px;"/>  

## 🔒 3 - How do you access my content in a secure way?

Unless you're using our hosting feature inside of Marketing Links, we don't host your content but stream directly from your CDN's servers.
- We are pretty flexible when it comes to authentication, and support several strategies: access token-based auth, header-based auth.
- We also have a system of signed URLs for your CDN to check and be 100% certain requests comes from Envoy.
- Finally, we're compatible with the DRM protection you have in place, you can give us 1 DRM certificate by DRM system (FairPlay, PlayReady, Widevine) for each video.

---

*👋 Say hi at info@envoy.is.*
