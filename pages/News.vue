<template>
  <div class="news">
    <section class="container">
      <div class="row mx-auto my-4">
        <div class="col-12 text-center">
          <h1>{{ pageTitle }}</h1>
          <p>The latest news from the global industry and how it impacts consumers.</p>
        </div>

        <div class="col-sm-12 col-md-10 col-xl-6 mx-auto bg-info">
          <h3 class="text-white pt-4 m-0">The Latest in WA Wine News</h3>
          <!-- CODE THAT CALLED THE ARTICLE CARD COMPONENT TO RENDER API DATA -->
          <!-- <section class="container mb-3" v-if="articles">
                <articleCard
                  v-for="article of articles"
                  :key="article.id"
                  :article="article"
                />
              </section>-->
          <!-- THIS IS THE NEW HARD-CODED SECTION TO WORK AROUND THE API PERMISSIONS ISSUE -->
          <div v-for="article in articles" :key="key">
            <article class="card p-3 m-3">
              <img :src="article.urlToImage" :alt="article.title" class="card__img img-fluid mb-4">
              <h5 class="card__title">{{ article.title }}</h5>
              <p class="card__author">{{ article.author }}</p>
              <p class="card__descriptor text-left">{{ article.description }} <a href="article.url">Read more at <span class="font-italic">{{ article.sourceName }}</span></a></p>
            </article>
          </div>
        </div>


        <div class="accordion col-sm-12 col-md-10 col-xl-6 mx-auto" role="tablist">
          <!-- for every story in the object, toggle between showing content and hiding it each time user clicks -->
          <b-card v-for="(story, key) in this.stories" :key="key" no-body class="border my-2">
            <b-card-header header-tag="header" class="pt-2 pb-0" role="tab">
              <b-button block v-b-toggle="'accordion-'+key" variant="light">
                <h5>{{ story.title }}</h5>
              </b-button>
            </b-card-header>
            <b-collapse :id="'accordion-'+key.toString()" accordion="my-accordion" role="tabpanel">
              <b-card-body class="text-left">
                <b-card-text>{{ story.p1 }}</b-card-text>
                <b-card-text>{{ story.p2 }} <a href="#"><span class="text-primary">Read more...</span></a></b-card-text>
              </b-card-body>
            </b-collapse>
          </b-card>
        </div>
      </div>
    </section>
  </div>
</template>

<script>
import axios from 'axios';
import articleCard from '@/components/articleCard.vue';

  export default {
  name: 'about',
  //THIS COMPONENT STYLED THE API DATA
  // components: {
  //   articleCard
  // },
  data () {
    return {
      pageTitle: 'Industry News',
      // loading: true,
      // articles: null,
      // errored: false,
      //THIS IS THE HARD-CODED DATA I COPIED FROM THE OBJECT RETURNED BY THE API
      articles: [
        {
          urlToImage: "https://ca-times.brightspotcdn.com/dims4/default/39dac7a/2147483647/strip/true/crop/6000x3150+0+425/resize/1200x630!/quality/90/?url=https%3A%2F%2Fcalifornia-times-brightspot.s3.amazonaws.com%2Fc3%2Fb9%2F646746f44f15b1834462ea826a93%2Fla-photos-1staff-621844-me-wineries-forego-2020-vintage-kkn-23203.JPG",
          title: "Disaster aid bill would compensate farmers for grape crops damaged by wildfires",
          author: "Sarah D. Wire",
          description: "Smoke-damaged grapes are cited as a crop potentially covered under a disaster aid in a bill that Congress is considering.",
          sourceName: "Los Angeles Times",
          url: "https://www.latimes.com/politics/story/2021-09-21/disaster-aid-bill-would-compensate-farmers-for-grape-crops-damaged-by-wildfires"
        },
        {
          urlToImage: "https://mma.prnewswire.com/media/1626889/Rivalry_Lives_On_Image.jpg?p=facebook",
          title: "The Rivalry Lives On: Canoe Ridge Vineyard And Waterbrook Winery Team Up With Cougar And Husky Athletics",
          author: null,
          description: "WALLA WALLA, Wash., Sept. 15, 2021 /PRNewswire/ -- While team pride runs strong, so does a statewide affinity for Washington wine. Canoe Ridge Vineyard and Waterbrook Winery have announced respective partnerships of University of Washington's Husky Athletics …",
          sourceName: "PRNewswire",
          url: "https://www.prnewswire.com/news-releases/the-rivalry-lives-on-canoe-ridge-vineyard-and-waterbrook-winery-team-up-with-cougar-and-husky-athletics-301377960.html"
        },
        {
          urlToImage: "https://thumbor.forbes.com/thumbor/fit-in/1200x0/filters%3Aformat%28jpg%29/https%3A%2F%2Fspecials-images.forbesimg.com%2Fimageserve%2F6134cbbc30a411e506ecd59e%2F0x0.jpg",
          title: "Washington State Wineries To Follow On Instagram During Harvest",
          author: "Leslie Kelly, Contributor",
          description: "Harvest season is a wonderful time to visit wine country. Here are some fun wineries to follow right now, including Brandi Carlile's inspiring label.",
          sourceName: "Forbes",
          url: "https://www.forbes.com/sites/lesliekelly/2021/09/07/washington-state-wineries-to-follow-on-instagram-during-harvest/"
        }
      ],
      stories: [
        {
          title: 'Wild Fires Across the West Raise Concerns Over Smoke Taint for a Fifth Consecutive Season - 27 August 2021',
          p1: 'Having seen a moderate start to the 2021 growing season, many hoped that the vintage would exhibit more concentration and greater purity than any other year in recent history. However, those hopes soon faded when extreme temperatures and tinder-dry weather sparked another season of record-breaking wildfires across the Canadian and American West.',
          p2: 'While the Washington State industry has largely escaped the major damage experienced across Oregon and California the last few years, many are worried that that earlier luck has run out. Speaking of Betz Family Winery\'s decision to discard the entire 2020 vintage, Head Winemaker Louis Skinner said, "We had hoped that our efforts to mitigate smoke taint in the final wines would be more effective than they were, but we eventually made the very tough call to scrap the whole vintage. Now we\'re in a position where we really can\'t have a second consecutive season impacted by smoke."'
        },
        {
          title: 'Record High Temps have PNW Growers Worried about 2021 Harvest - 5 July 2021',
          p1: 'As temperatures in several parts of the Pacific Northwest have smashed decades-old high temperature records and set more for how long those high temps were sustained, growers have begun to worry about the effect of the extreme heat on the vines.',
          p2: 'Although this latest spell struck late enough in the season that it did not impact flowering or fruit set, it still has the potential to inflict sunburn damage on lighter-skinned varieties. "To make matters worse, in some vineyards we intentionally defoliated to allow better airflow through the fruiting zone," said Dick Boushey of Boushey Vineyards. "We already had a light harvest combined with scattered zones of smoke damage in 2020, and we can\'t afford a second year in a row of low yields. Had we known this long and extreme of a heat wave was coming, we may have made some different decisions."'
        },
        {
          title: 'COVID Travel Restrictions Continue to Pose Serious Challenges for Worldwide Industry Workforce - 14 May 2021',
          p1: 'As Spring temperatures spread across the Northern Hemisphere, and Australia and New Zealand welcomed each other into a mutual travel bubble, many were hopeful that the darkest days of the pandemic were drawing to a close. But even as accelerated vaccine rollout in the United States and several European countries gave many in the wine industry hope for a normal Harvest 2021, challenges in Southern Hemisphere wine regions spelled trouble for an industry that relies heavily on international workers traveling from harvest to harvest.',
          p2: 'Prior to Vintage 2021 we had only just lifted the ban on travel from Australia," said Stu Marfell of Foley Wines Ltd in Marlborough, New Zealand. "We knew that borders would never open for workers from across Europe and North America in time, so we had to scramble and find help locally." While wine producers in Australia and New Zealand ultimately made it through the February-April season with only local help, North American producers, who had another six months before their own harvest, hoped they wouldn\'t have to. But even as many more in the general population become fully vaccinated, worldwide COVID policies continue to impact U.S. Embassy operations overseas. With several Embassies and Consulates still in complete lock-down, much of the international workforce is unable to schedule the in-person interview appointments required for attaining a J-1 visa for seasonal work in the United States.'
        },
        {
          title: 'Late Season Frost Threatens Loss of an Entire French Vintage - 15 April 2021',
          p1: 'Many in Western Europe were thrilled with the unusually early warm spring weather. As temperatures hit 82F (28C) in late March, grapes and other crops across France began to flower, kicking off their growing season unseasonably early. But it was only a matter of days before a cold spell struck, and the whole industry was threated by a late-season frost.',
          p2: 'Early assessments estimate that as much as 80% of the 2021 crop could be damaged or lost, dealing another devastating blow to an industry still trying to climb back to normalcy post-pandemic. "Even with insurance and governement subsidies, we can\'t recover from a second year with less than half our typical income," said Jean-Louis Chave of the Hermitage AOC.'
        }
      ]
    }
  },
  //THIS IS THE FUNCTION THAT PULLS DATA FROM THE API, BUT ONLY WORKS ON LOCALHOST:3000
  // mounted () {
  //   console.log('mounted is running')
  //   axios
  //   .get('https://newsapi.org/v2//everything?q=%22washington%20wine%22&sortBy=publishedAt&apiKey=eb66c22fa9ec418094bb0e52e9009a6a')
  //   .then(response => {this.articles = response.data.articles
  //     console.log(response)} )
  //   .catch(error => {
  //     console.log(error)
  //     this.errored = true
  //   })
  //   .finally(() => this.loading = false)
  // }
}
</script>
