# 🌍 AI & its impact on the environment - A Data Driven View

Hello everyone! I have heard many claims about AI's devastating impact on the environment; as a keen advocate of AI and as someone who’s passionate about living on a healthy, green planet - this has proposed a conundrum to me. So, I decided to investigate further… 🟩🌍


## 💡 A bit of research; grabbing some numbers

In short - the reasoning behind AI's perceived negative impact on the environment comes from the massive data centre uses; the electricity to power them and water to cool them down.

However - this situation of course applies to countless technologies - just think about the processing required behind getting TikTok, YouTube, Netflix, Spotify and Zoom to run in our everyday use...

Taking a look at the data, I’ve pulled in estimations for:

1. Typical energy usage for various AI queries plus other technologies*, and every day activities.
2. The same for training AI
3. The carbon emissions per unit of energy, by different regions
4. Water Usage Effectiveness of Microsoft Data Centres**

> [!info]
>*These numbers carry a significant margin of error; data-centre energy totals are used to work backwards; spreading that power across networks, devices, users, and time to land on a rough cost per operation per user. They represent ball-park figures only; **these numbers are directional, not precise. **The goal is scale, not accuracy.
> **OpenAI is powered by Microsoft Azure Data Centres; WUE can be measured in Litres per kilowatt hour to detect the water required in datacenter operation. 

To see the exact values and their sources, please expand the content below.

<details>
<summary>Estimations used for this investigation</summary>
```python 
> # AI usage, all measured in kWh
> chatGPT_chat=0.0003 # source: https://epoch.ai/gradient-updates/how-much-energy-does-chatgpt-use
> image_generation=0.011 #source: https://www.slashgear.com/1696332/ai-image-generation-how-much-energy-used/
> min_of_sora_2_video=0.140 # source: https://www.reddit.com/r/theydidthemath/comments/1dnpw9q/comment/la5zw2c/
> small_text_query=0.0001
> deep_research_chatGPT_query=0.01
> reasoning_chatGPT_request=0.02
> codex_code_completion=0.003
> # source: https://www.abcmoney.co.uk/2025/06/gpt-5-development-sparks-fresh-debate-over-ais-carbon-footprint/
> GPT_5_training_energy = 3500 * (10**3)
> # source: https://energyguide.org.uk/how-much-electricity-do-appliances-use/
> ten_minute_shower=1.6
> iron_thirty_minutes=1.3
> fridge_day=1.2
> hair_drier_ten_minutes=0.2
> electric_hob_twenty_minutes=0.6
> # source: https://www.autohit.co.uk/electric-car-efficiency-uk-2025-real-driving-costs-per-mile/
> driving_electric_car_five_minutes=0.625
> # source: https://www.bbc.co.uk/food/articles/energy_saving_tips
> boiling_kettle_for_one_tea = 0.07
> oven_for_thirty_minutes=1.51
> # source: https://www.comparitech.com/tv-streaming/internet-energy-saving-study/
> netflix_one_hour = 0.053
> streaming_music_one_hour = 0.013
> # source: https://www.forbes.com/sites/johnkoetsier/2025/12/03/new-data-ai-is-almost-green-compared-to-netflix-zoom-youtube/
> youtube_one_hour = 0.12
> # source: https://store.chipkin.com/articles/did-you-know-it-takes-00003-kwh-per-google-search-and-more
> google_search = 0.0003
> zoom_call_one_hour = 0.2
> scrolling_social_media_one_hour=0.42
> youtube_one_hour=0.12
> #source: https://adam.holter.com/why-your-chatgpt-prompt-uses-half-the-energy-of-a-tiktok-video/
> tiktok_per_minute=0.6/1000
> # kg of CO2 produced per kwh, source: https://ourworldindata.org/grapher/carbon-intensity-electricity?mapSelect=USA~GBR~SWE
> energy_emission_coefficients = {
>     "United States": 0.384,
>     "United Kingdom": 0.211,
>     "Sweden": 0.036,
>     "India": 0.708,
>     "Australia": 0.552,
>     "New Zealand": 0.120,
> }
> # litres of water used per kwh
> #ource: https://datacenters.microsoft.com/sustainability/efficiency/
> US_Data_Center_L_per_KWH = 0.3
> # litres produced examples
> one_minute_showering = 16 # source: https://www.ariston.com/en-me/the-comfort-way/news/how-much-water-is-consumed-for-a-shower/
> # kg of CO2 produced
> driving_one_hundred_miles = 30 #source: https://www.carbonfootprint.com/reduce_vehicle.html
> flying_edi_to_beijing_return = 3000 # source: https://co2.myclimate.org/en/portfolios?calculation_id=8369846&localized_currency=GBP
> eating_10_beef_burgers=30.68 #source: https://foodfootprint.nl/en/foodprintfinder/hamburger/
> average_uk_gas_boiler_emissions_one_year = 2200
> # much bigger numbers - kg of CO2
> GPT_5_training_emissions = GPT_5_training_energy * energy_emission_coefficients["United States"]
> thousand_hour_private_jet = 2430*(10**3) # source: https://sustainabletravel.org/our-work/carbon-offsets/calculate-footprint/
> typical_blockbuster_film = 4700 * (10**3) # source: https://zipdo.co/sustainability-in-the-motion-picture-industry-statistics/
> US_military_in_one_hour = (131500 * (10**3)) / 24 #source: https://www.theguardian.com/environment/2025/may/30/donald-trump-geopolitics-could-deepen-planetary-catastrophe-expert-warns?utm_source=chatgpt.com
> building_london_cheesegrater = 92210 * (10**3) # source: https://finance-commerce.com/2019/06/the-carbon-footprint-of-modern-construction-is-huge/?utm_source=chatgpt.com
> average_f1_race_2024 = (168720 * (10**3)) / 24 # source: https://www.formula1.com/en/latest/article/formula-1-on-track-to-be-net-zero-by-2030-with-26-reduction-in-carbon.4p2vZMDrgDu6lVHLvOcLPy?utm_source=chatgpt.com
> hundred_brits_average_emissions = 8.4*100*(10**3) # source: https://footprint.wwf.org.uk/
> average_UK_home_per_year = 2700*energy_emission_coefficients["United Kingdom"] #source: https://www.ovoenergy.com/guides/energy-guides/how-much-electricity-does-a-home-use
> # water usage, in litres
> GPT_5_water_usage = GPT_5_training_energy * US_Data_Center_L_per_KWH
> # source: https://news.trust.org/item/20120724100000-mf6n8?utm_source=chatgpt.com
> pair_of_jeans=8000
> one_kilo_of_ketchup=530
> one_burger_patty=2500
> olympic_pool=2.5*(10**6)
> bath=100
> # source: https://watercalculator.org/water-footprint-of-food-guide/
> one_hundred_grams_chocolate=1800
```
</details>

## 🔌 Energy usage of AI

First of all, let's look how much energy (measured in kWh) is typically used by different AI requests and how this compares in terms we know and understand.

### How requests compare

```adf 
{"type":"mediaSingle","attrs":{"layout":"wide","width":964,"widthType":"pixel"},"content":[{"type":"media","attrs":{"width":2083,"alt":"image-20251229-190707.png","id":"c9059cfa-67e8-4c8c-8c11-a43d414ff749","collection":"contentId-1987118963","type":"file","localId":"48d11c0d-a112-4205-9038-2bbf9eb1dfe5","height":707}}]}
```

Clearly there is **significant variation in energy usage depending on how we use AI**. Complexity drives energy usage massively.

The energy usage of 100 simple queries would roughly match a deep research question; and 7 of those roughly matches the energy required for 30 seconds of Sora 2 AI Video. 

It's good to see how different requests compare to themselves in AI - but what does this mean in terms we'd understand?

> [!info]
> An example simple query could be *"What's the Capital of France" *and a deep reasoning question could be *"Analyse and explain the footfall of a typical Gregg's in London".*

### Comparing to everyday home uses

Firstly, how about looking at comparing these to everyday home appliances

```adf 
{"type":"mediaSingle","attrs":{"layout":"wide","width":1004,"widthType":"pixel"},"content":[{"type":"media","attrs":{"width":2004,"alt":"image-20251229-190841.png","id":"2b8e9131-6a5c-4438-b940-8bec335a1dd0","collection":"contentId-1987118963","type":"file","localId":"f69d7d2f-cd87-42e6-83af-75779c8b0a30","height":717}}]}
```

As we can see; **regular daily and some intense uses of AI is very modest compared to everyday household examples**. Even 233 typical ChatGPT messages would roughly be less than the energy required for boiling 1 cup of water. 

So; if AI isn't the energy villain in our homes, what about when we compare it to other digital technologies?

### Comparing to other technologies

And finally - let's see how AI compares to other technologies

```adf 
{"type":"mediaSingle","attrs":{"layout":"wide","width":1004,"widthType":"pixel"},"content":[{"type":"media","attrs":{"width":2067,"alt":"image-20251229-190938.png","id":"998fee73-dd7f-4250-b372-c202f10069ee","collection":"contentId-1987118963","type":"file","localId":"d424b3de-ba65-4b29-8e3a-4f882edf2d09","height":696}}]}
```

> [!warning]
> Again, this data is not concrete; do not take any comparisons as factual or scientific.

**Typical AI uses seem to be light-weight in the tech world**. The main culprits are with Zoom and Social Media and although AI's energy usage is significant - it is not nothing; generating video especially could be a concern if done many times a day. 

It makes sense when you think about it: a single scroll through social media requires on-demand video streaming with heavy, personalised algorithms & think about what must be required to stream that 4K fireplace on YouTube. 

```adf 
{"type":"heading","attrs":{"level":2,"localId":"01562a15-b1d4-4e14-a26e-c29425f6e7a2"},"content":[{"type":"emoji","attrs":{"id":"f47b716c-6c9e-4b84-b6ec-c0f095fc3ae3","text":":cloud:","shortName":":cloud:","localId":"792e7032-0e04-4684-a7ae-16895e6027b5"}},{"text":" But what about carbon emissions?","type":"text"}]}
```

With AI and tech, **carbon emissions come from the electricity powering the data centres**. The greener the energy, the smaller the footprint — luckily, we actually have metrics to measure this.

```adf 
{"type":"mediaSingle","attrs":{"layout":"wide","width":978,"widthType":"pixel"},"content":[{"type":"media","attrs":{"width":2090,"alt":"image-20251229-191124.png","id":"076ef8c0-f122-4c5d-9ccc-d77d3c627415","collection":"contentId-1987118963","type":"file","localId":"a2f53018-edfc-45c8-888e-26588618a82b","height":623}}]}
```

**Geography makes a huge difference**.

- The same task in India can produce nearly 20× the emissions of Sweden
- US data centres emit roughly double what the UK does for the same work.

```adf 
{"type":"mediaSingle","attrs":{"layout":"center","width":760,"widthType":"pixel"},"content":[{"type":"media","attrs":{"width":925,"alt":"image-20260106-104026.png","id":"2ac81ce1-65a0-4528-9e4b-b71ddefcb111","collection":"contentId-1987118963","type":"file","localId":"f7979607-7297-4909-9a89-e770cd872455","height":439}},{"type":"caption","attrs":{"localId":"47837f13-2c01-48d8-8845-b65e93dbb0cc"},"content":[{"text":"Extract Our World in Data; carbon intensity, see full ","type":"text"},{"text":"world map view","type":"text","marks":[{"type":"link","attrs":{"href":"https://ourworldindata.org/grapher/carbon-intensity-electricity?mapSelect=USA~GBR~SWE"}}]},{"text":" for more.","type":"text"}]}]}
```

### CO2 from individual uses of AI, large scale. 

So, assuming all processing is done at typical UK data centres - I want to build a view of large scale view of AI use cases over a year and how much CO2 this produces. I use a couple examples as:

#### AI Power User, over 1 year:

- 10,000 ChatGPT messages
- 2,000 deep reasoning requests
- 1000 Code generations
- 50 AI images generated

#### Average AI User, over 1 year

- 300 chat queries
- 1,000 ChatGPT messages
- 25 deep reasoning requests

> [!note]
> According to ChatGPT 2025 unwrapped; I received 4,784 messages which is in the top 5% worldwide.

Let's see what this all produces:

```adf 
{"type":"mediaSingle","attrs":{"layout":"wide","width":978,"widthType":"pixel"},"content":[{"type":"media","attrs":{"width":2093,"alt":"image-20251229-191317.png","id":"68313017-ea2d-4a45-83a9-99c76a105b32","collection":"contentId-1987118963","type":"file","localId":"162ff388-0093-4667-b834-5cc02d66bffe","height":699}}]}
```

There's massive difference between being a power user compared to your average user, video generation is significant. 

### Compared to more, everyday, use cases

If most users are between the 100g to 10kg of CO2 produced; let's see how these numbers compare in context which we understand. 

```adf 
{"type":"mediaSingle","attrs":{"layout":"wide","width":974,"widthType":"pixel"},"content":[{"type":"media","attrs":{"width":2114,"alt":"image-20251229-191408.png","id":"83ba2c8d-6d17-4da0-8866-46300bfe7010","collection":"contentId-1987118963","type":"file","localId":"70f010ac-006a-4ca7-a447-bc7aaabce369","height":1050}}]}
```

Here's an interesting graph (or at least it is to me);

- The 120g of CO2 from an average AI user is *almost* insignificant on this graph
- As before; the much higher end of AI uses compare average everyday uses of existing tech
- However, **all these emissions from such technologies over a year can be trumped by a typical 50 mile car journey** (e.g. a return trip from Edinburgh to Falkirk) or just from the process of making 5 burger patties (e.g. someone's big and not-very-tasty dinner).

The major factor here is how green the energy source is; the above is assuming UK electricity - but the picture would be completely different for data centres in Sweden.

```adf 
{"type":"heading","attrs":{"level":2,"localId":"5f21d261-3e0b-4deb-9d6c-8a5f4f68f7c1"},"content":[{"type":"emoji","attrs":{"id":"1f30a","text":"🌊","shortName":":ocean:","localId":"094e9965-51cc-412f-a783-080001fbda61"}},{"text":" What about water usage?","type":"text"}]}
```

We do hear a lot of the water required in data centre cooling; again this is region dependant and well document by Microsoft in their [data centre efficiency article](https://datacenters.microsoft.com/sustainability/efficiency/).

> [!info]
> In this exercise, we're needing the *Water Usage Effectiveness* measured in Litres required per kWh of electricity. We're assuming the global average of 0.3L/kWh.

```adf 
{"type":"mediaSingle","attrs":{"layout":"wide","width":968,"widthType":"pixel"},"content":[{"type":"media","attrs":{"width":2096,"alt":"image-20251229-191709.png","id":"2d8a527a-20b9-4ef2-81f8-fd41dc358183","collection":"contentId-1987118963","type":"file","localId":"3319141d-4487-4464-a458-2776a3bb4caf","height":610}}]}
```

Data centre cooling seems efficient at a scale of high-end use; **it would take roughly 400 messages to ChatGPT to waste an espresso-cup sized amount of water** and we have a similar story for other technologies. On a personal scale, the water usage from AI or any technology is not a concern.

```adf 
{"type":"heading","attrs":{"level":2,"localId":"1ecee0a3-3e8e-43c8-8997-20bfb0f2a25e"},"content":[{"type":"emoji","attrs":{"id":"1f419","text":"🐙","shortName":":octopus:","localId":"d1fa62bb-d629-4ffd-97bd-67c725d13743"}},{"text":"  A quick note on Claude","type":"text"}]}
```

Many of us engineers are using Claude in our tasks; and this method appears to be constantly reasoning and producing code - so the some metrics like *number of chats* wouldn’t work here. But **we can see the token usage**…

Taking some more estimates - we can use a rule of thumb of: **10,000 tokens roughly consumes 50Wh of energy which emits 10.5g of CO2 **(UK based energy), this very roughly equates to:

- Streaming Netflix for ~1 hour
- Showering for ~20 seconds (electric shower)
- Driving ~50 metres in a typical petrol car

> [!info]
> This estimate I just checked with ChatGPT ([conversation](https://chatgpt.com/share/e/69613398-2cec-8011-a50e-1aff30df30da)); feel free to research & correct me!

```adf 
{"type":"heading","attrs":{"level":2,"localId":"289b650e-3895-4153-94e9-65612acdfe9a"},"content":[{"type":"emoji","attrs":{"id":"add34d79-8667-4380-89f3-86d98ad75125","text":":ai_technology:","shortName":":ai_technology:","localId":"f160c570-10b2-4ec0-9c26-d8a96bf7bd1f"}},{"text":" Don’t forget - training AI","type":"text"}]}
```

So why all hysteria about AI being bad for the environment? Well an elephant in the room so far ignored is **what is required when training AI,** and this is significant.

> [!note]
> The exact details of training a GPT-5-scale model are not public, but it involves running large GPU clusters continuously for weeks to optimise billions of parameters over vast datasets. A significant amount electricity is used and this is largely carried out in the United States.

This is a massive operation. We went from talking about watt hours, millilitres and grams of CO2 to: gigawatts, mega-litres, and thousands of metric tonnes of CO2 emitted.

No need for a graph; **in the tech world, only training AI is capable of this.**

Let's see how the demand compares to other large-scale emitters of CO2; (assuming US-based data centres).

```adf 
{"type":"mediaSingle","attrs":{"layout":"wide","width":968,"widthType":"pixel"},"content":[{"type":"media","attrs":{"width":2120,"alt":"image-20251229-191853.png","id":"e391a480-26b7-407a-a010-41c8406a983c","collection":"contentId-1987118963","type":"file","localId":"b9ac88aa-1218-429e-8b26-273ef4bdafd8","height":784}}]}
```

Training large AI models produces substantial emissions; **even more than a typical private jet flying non-stop for 500 hours.**

However, this is a one-off exercise where a trained model is then used by millions globally - the emissions are significantly less than those from producing a movie or from a typical F1 race.

### And its water usage

Again; this will follow the same pattern as above - the extreme amount of computation would require an extreme amount of water for cooling, the likes of which has never been needed for Zoom or Social Media.

Again; let's see how this compares to other gotcha's we may not expect:

```adf 
{"type":"mediaSingle","attrs":{"layout":"wide","width":988,"widthType":"pixel"},"content":[{"type":"media","attrs":{"width":2122,"alt":"image-20251229-192039.png","id":"7c54ad57-b2b2-4737-81f5-875ac43490b3","collection":"contentId-1987118963","type":"file","localId":"85ef0786-2fe2-40a6-83b7-5aa09471a2dc","height":773}}]}
```

The fact that training an GPT model uses more water than 10,000 baths is again - crazy. 

Though we have more concerning consumers of our water - roughly 8,000L goes into producing a pair of jeans and 2,500L for the process of producing a single burger patty.

> [!note]
> The AI autocomplete recommends I write that the water usage of AI is negligible... I wouldn't go that far!

```adf 
{"type":"heading","attrs":{"level":2,"localId":"70025bf7-c633-43bd-a354-26c9762dd6c9"},"content":[{"type":"emoji","attrs":{"id":"1f30d","text":"🌍","shortName":":earth_africa:","localId":"f75c11c2-516f-42c4-9879-8e6479ad323f"}},{"text":" Closing thoughts & how we can help","type":"text"}]}
```

This blog is not a deep-dive; I’ve ball-parked AI’s impact to the environment, compared this to other activities, and have come to the conclusion that *it doesn’t seem all that bad* in context.

If you’re considering cutting back on AI to help the planet; it is my opinion that this would not be effective; there are far bigger and easier gains outwith AI. See what [WWF say about it](https://www.wwf.org.uk/thingsyoucando), and if energy usage is the worry - perhaps consider the impact of streaming video or scrolling social media.

> [!note]
> To be frank, the real discussion shouldn’t be about using AI - it should be about how green its energy is. In other words, **AI isn’t bad for the environment, powering it with fossils fuels is. **This should be the debate.

So, how can we help? It’s not for me to say here, but it’s always good practise to educate yourselves; be a little skeptical, have some conversations, and do your own research. As a few pointers:

- Chat to Ecosia’s AI: [https://www.ecosia.org/ai-search](https://www.ecosia.org/ai-search) (backed by renewable energy)
- Consider the book: [https://www.goodreads.com/book/show/7230015-how-bad-are-bananas](https://www.goodreads.com/book/show/7230015-how-bad-are-bananas)  (I’ve not read this yet; but considers and discusses carbon footprint of all our everyday activities)
- Checkout our in-house sustainability Slack channel: [https://skyscanner.slack.com/archives/C4MVDMPCL](https://skyscanner.slack.com/archives/C4MVDMPCL) 

```adf 
{"type":"paragraph","attrs":{"localId":"ccc0ef59-b155-4a89-9f6f-88228d7adbb4"},"content":[{"text":"… Anyway, that’s me. I hope this has been a useful and informative read! Adios ","type":"text"},{"type":"emoji","attrs":{"id":"262e","text":"☮️","shortName":":peace:","localId":"f4e55cc5-7dc5-4f86-8730-4e5fe59458ff"}},{"text":" ","type":"text"}]}
```


