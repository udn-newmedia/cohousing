<template>
  <div id="app">
    <div class="timeline">
      <hr>
    </div>
    <Indicator></Indicator>
    <Headbar>
      <a slot="logo" href="https://vision.udn.com/"><img class="other_logo" src="../static/visual-logo.png" alt="聯合報願景工程"></a>
      <a href="#"><b>我和我的高齡室友</b></a>
      <a href="#">德國多代共居</a>
      <a href="#">世代共融系列報導</a>
    </Headbar>
    <Cover class="cus_cover_bg" src="@/../static/image_0812/cover_m.jpg" srcWeb="@/../static/image_0812/cover_pc.jpg"
    useArrow="yes" useHint="yes" arrow-color="#fff">
      <h1 class="cus_cover_title">「我和我的高齡室友」<br>跨世代共居如何迸出奇異火花</h1>
    </Cover>
    <ContentContainer>
      <Share href="https://udn.com/upf/newmedia/2018_data/cohousing/index.html"></Share>
      <p><br></p>
      <div ref="introSec" class="animated" :class="{'fadeInUp': introShow}">
        <p>今年3月，台北市陽明老人公寓推動「青銀共居」實驗，仿照荷蘭安養院「以工換宿」計劃，開放8名文化大學學生入住，每個月只要陪伴老年人下棋、唱歌、教導3C等，完成20小時服務時數，即可以3000元入住獨立套房。希望促進跨世代經驗交流，營造共融生活。</p>
        <p><br></p>
        <p>聯合報系《願景工程》團隊走進陽明老人公寓，紀錄兩代之間的混齡共居生活，相差5、60歲的「鄰居朋友」相處起來會擦出什麼火花？並從他們真實的社群聊天對話中，看不同世代如何透過3C科技、社群網路交流，一窺他們日常中最真誠自然的互動。</p>
      </div>
      <p><br></p>
    </ContentContainer>
    <Chat></Chat>
    <ContentContainer class="forceContentPaddingZero">
      <FixLineList></FixLineList>
      <div id="linePaper" class="lineWrapper">
        <div class="lineHead" id="ppl_1">
          <div class="line_profile">
            <img src="../static/image_0812/meian.png" alt="陳玫安">
          </div>
          <div class="line_title">
            <h4>陳玟安 文化大學心輔系三年級</h4>
            <span>2018年8月24日</span>
          </div>
        </div>
        <p><br></p>
        <h4><b>【用Line揪爺爺奶奶出來玩】</b><img src="@/../static/emote/1f609.png"></h4>
        <p><br></p>
        <p>會想申請青銀共居，是因為我很喜歡跟老年人相處。我跟自己的阿公阿嬤感情很好，但是跟公寓的爺爺奶奶相處又是不同感覺，畢竟不是家人，剛開始會有距離感。但透過平常吃飯、活動時，多去打招呼，爺爺奶奶認識你之後，就會開始關心你。其實跟長輩建立關係不難，只是需要時間。</p>
        <p><br></p>
        <p>像我會透過Line和爺爺奶奶互動，例如前一天Line他們「明天有活動，爺爺奶奶要來參加嗎？」或是直接敲門拜訪，拉他們出來參加活動。有時候長輩不是不想參加，只是有點懶、或是人很多會有點排斥，但只要有人拉他們，他們參與意願就會比較高。</p>
        <p><br></p>
        <Carousel :carouselMenu="MeiAnCarouselMenu"></Carousel>
        <p><br></p>
        <p>住在這裡五個多月，我發現爺爺奶奶開始跨出生活圈，會互相邀約去參加活動。這裡的老人家很多人都會日語，我也有輔修日文，所以溝通更沒有障礙，爺爺奶奶也會邀我參加他們的活動。</p>
        <p><br></p>
        <p>有位爺爺原本不太愛出門，後來也被我們的氣氛感染了，他說「我也要參加，因為你們都要參加」，聽到這句話時，內心真的很感動。</p>
        <p><br></p>
        <p>我覺得老人家最需要的是耐心陪伴，他們很期盼我們不時地出現。有時候下課回來，爺爺奶奶會說「很久沒看到妳」，但其實我們昨天才見過面。聽到時感覺心裡有點酸，會想起自己的阿公阿嬤，平常沒有機會這麼頻繁接觸，他們一定也很想我吧。</p>
        <p><br></p>
        <p class="hash_tag">爺爺奶奶留門縫代表歡迎拜訪<img src="@/../static/emote/2763.png"></p>
        <p class="hash_tag">跟長輩之間的小默契</p>
        <p><br></p>
      </div>
      <div class="lineWrapper forcePaddingZero">
        <TweenVideo :src="TweenVideoSrc[0]"></TweenVideo>
      </div>
      <div class="lineWrapper">
        <p><br></p>
        <div class="lineHead" id="ppl_2">
          <div class="line_profile">
            <img src="../static/image_0812/anna.png" alt="謝安娜">
          </div>
          <div class="line_title">
            <h4>謝安娜 陽明老人公寓長輩</h4>
            <span>2018年8月24日</span>
          </div>
        </div>
        <p><br></p>
        <h4><img class="emoImg" src="@/../static/emote/1f44d.png"><img src="@/../static/emote/1f44d.png"><img src="@/../static/emote/1f44d.png"><b>【我給每個孩子一顆彩蛋】</b></h4>
        <p><br></p>
        <p>青銀共居對我來說不是一件新鮮的事。我年輕時在文化大學當行政人員，是天主教弘道社指導老師，所以我跟年輕人的關係一直沒有斷。當時社團學生，來我家當我孩子的家教，我知道他們很多人念書很苦，每次一來我都煮大鍋菜，看他們吃飽，我也覺得很幸福。</p>
        <p><br></p>
        <p>但當時的年輕人，跟現在的年輕人又不一樣。現在的年輕人更花俏，懂電腦啊，我退休時還在用word2007，現在他們已經教我上雲端了。</p>
        <p><br></p>
        <p>最讓我感動的是一位社福系學生劉莉君，她是第一批參加青銀共居的學生，我做了很多復活節彩蛋，她幫我成立一個粉絲專頁，讓我在上面交朋友，寫蛋的故事。後來她畢業，跟我道別，我很捨不得。不過沒關係，有新同學，希望他們能幫忙把我做的蛋，推上國際舞台！<img class="emoImg" src="@/../static/emote/1f525.png"><img class="emoImg" src="@/../static/emote/1f525.png"><img src="@/../static/emote/1f525.png"></p>
        <p><br></p>
        <Carousel :carouselMenu="AnnaCarouselMenu"></Carousel>
        <p><br></p>
        <p>現在我退休了，孩子也都長大結婚生子，我的先生比較早走，就剩我一個人了。我常在想，人一生中有很多重要的時刻，我走到這個階段，該好好想想在我有限的生命裡我能做什麼。</p>
        <p><br></p>
        <p>住在這裡的每個孩子，我都給他們一顆蛋，他們都放在房間裡。雖然我的腿已經不好使，但我希望我還可以用，我想要自己能夠被用。</p>
        <p><br></p>
        <p class="hash_tag">每一顆蛋都是祝福<img class="emoImg" src="@/../static/emote/1f60d.png"><img class="emoImg" src="@/../static/emote/1f60d.png"><img src="@/../static/emote/1f60d.png"></p>
        <p class="hash_tag">分享快樂是抗老的最好方法</p>
        <p><br></p>
        <p><br></p>
      </div>
      <div class="lineWrapper forcePaddingZero">
        <TweenVideo :src="TweenVideoSrc[1]"></TweenVideo>
      </div>
      <div class="lineWrapper">
        <p><br></p>
        <div class="lineHead" id="ppl_3">
          <div class="line_profile">
            <img src="../static/image_0812/sutou.png" alt="王斯特">
          </div>
          <div class="line_title">
            <h4>王斯特 文化大學政治系三年級</h4>
            <span>2018年8月24日</span>
          </div>
        </div>
        <p><br></p>
        <h4><b>【老人家不是都一個樣子】</b><img class="emoImg" src="@/../static/emote/1f601.png"><img class="emoImg" src="@/../static/emote/1f601.png"><img class="emoImg" src="@/../static/emote/1f601.png"><img class="emoImg" src="@/../static/emote/1f601.png"><img src="@/../static/emote/1f601.png"></h4>
        <p><br></p>
        <p>住進陽明老人公寓已經五個月了，一開始會想申請，是因為覺得這裡CP值很高，一個月3000元，同學都羨慕，同樣規格在外面租房子，大概要一萬塊吧。</p>
        <p><br></p>
        <p>另一方面，也是因為爸媽支持。我家住台中，爸爸在我小時候，因為工作的關係，曾在台北住過一陣子，他當時30歲，跟一位7、80歲的老房東奶奶同住，算是青銀共居先驅吧。是爸媽鼓勵我，我才願意來申請。</p>
        <p><br></p>
        <p>服務老人家對我來說也是蠻新的體驗，因為我外公外婆在我出生前就走了，爺爺奶奶也在我小時候就過世，我沒機會好好給他們被當孫子疼愛。</p>
        <p>
          <img class="emoImg" src="@/../static/emote/1f64f.png">
          <img class="emoImg" src="@/../static/emote/1f64f.png">
          <img class="emoImg" src="@/../static/emote/1f64f.png">
          <img class="emoImg" src="@/../static/emote/1f64f.png">
          <img class="emoImg" src="@/../static/emote/1f64f.png">
          <img class="emoImg" src="@/../static/emote/1f64f.png">
          <img class="emoImg" src="@/../static/emote/1f64f.png">
          <img class="emoImg" src="@/../static/emote/1f64f.png">
          <img class="emoImg" src="@/../static/emote/1f64f.png">
          <img class="emoImg" src="@/../static/emote/1f64f.png">
          <img class="emoImg" src="@/../static/emote/1f64f.png">
          <img class="emoImg" src="@/../static/emote/1f64f.png">
        </p>
        <p><br></p>
        <Carousel :carouselMenu="SterCarouselMenu"></Carousel>
        <p><br></p>
        <p>我也愛看老電影，巨人啊、北非諜影等。有位拿蘋果手機的奶奶，感覺年輕時也是文青，跟我聊到電影，突然就很有話題。還有位爺爺年輕時是留美的，個性比較開放，研究的東西跟我主修的政治相關，跟他聊天感覺更是沒有距離。</p>
        <p><br></p>
        <p>以前我也有很多刻板印象，以為老人家就是很寂寞等著人去照顧；但其實他們會自己安排生活，有的忙到不可開交。</p>
        <p><br></p>
        <p>你以為老人家都晚餐吃飽就回去睡覺，不是，有位爺爺跟我看世界盃 ，法克大戰，看到凌晨一點。有些爺爺奶奶也跟我一樣，半夜才睡，睡到中午才醒，他們的生活也一點都不無聊，很會找事做。<img src="@/../static/emote/1f602.png"><img src="@/../static/emote/1f602.png"><img src="@/../static/emote/1f602.png"></p>
        <p><br></p>
        <p class="hash_tag">爺奶說我穿得很帥</p>
        <p class="hash_tag">老人家很能接受新事物<img class="emoImg" src="@/../static/emote/1f633.png"><img class="emoImg" src="@/../static/emote/1f633.png"><img class="emoImg" src="@/../static/emote/1f633.png"></p>
        <p><br></p>
      </div>
      <div class="lineWrapper forcePaddingZero">
        <TweenVideo :src="TweenVideoSrc[2]"></TweenVideo>
      </div>
      <div class="lineWrapper">
        <p><br></p>
        <div class="lineHead" id="ppl_4">
          <div class="line_profile">
            <img src="../static/image_0812/yuchen.png" alt="林育甄">
          </div>
          <div class="line_title">
            <h4>林育甄 文化大學心輔系三年級</h4>
            <span>2018年8月24日</span>
          </div>
        </div>
        <h4><b>【爺爺奶奶最需要家人的關心】</b></h4>
        <p>
          <img class="emoImg" src="@/../static/emote/2764.png">
          <img class="emoImg" src="@/../static/emote/2764.png">
          <img class="emoImg" src="@/../static/emote/2764.png">
          <img class="emoImg" src="@/../static/emote/2764.png">
          <img class="emoImg" src="@/../static/emote/2764.png">
          <img class="emoImg" src="@/../static/emote/2764.png">
          <img class="emoImg" src="@/../static/emote/2764.png">
          <img class="emoImg" src="@/../static/emote/2764.png">
          <img class="emoImg" src="@/../static/emote/2764.png">
          <img class="emoImg" src="@/../static/emote/2764.png">
          <img class="emoImg" src="@/../static/emote/2764.png">
          <img class="emoImg" src="@/../static/emote/2764.png">
          <img class="emoImg" src="@/../static/emote/2764.png">
        </p>
        <p>雖然我才搬進陽明老人公寓一個月，但我覺得跟這裡的老人家，比起跟同學、其他大人相處起來關係完全不同。跟爺爺奶奶互動的時候，可以感覺到他們每一個問候都是很真心的。人與人溝通，真誠是最珍貴的，我覺得公寓這裡是很難得的氣氛。</p>
        <p><br></p>
        <p>我很喜歡這裡，回家跟爸媽說「乾脆全家一起搬來」，他們居然也很樂意。很多人覺得住在老人院，好像很悲情，但我來這裡之後發現，老人家其實有很多自己想做的事情，生活得很有目標，住在老人公寓也可以很幸福。</p>
        <p><br></p>
        <Carousel :carouselMenu="YuiChenCarouselMenu"></Carousel>
        <p><br></p>
        <p>我覺得爺爺奶奶最需要的是陪伴。有時候跟爺爺奶奶聊天，安靜下來的時候，會看見老人家脆弱的樣子，其實他們最需要的是家人、孩子的關心。</p>
        <p><br></p>
        <p>住我隔壁的一位奶奶，在我來的第一天就拉著我的手，說她兒子答應她要來教公寓的大家打桌球，奶奶說的時候眼睛裡閃著光芒。但後來有天去拜訪奶奶，問到桌球的事，她說兒子太忙了，只能作罷。我們當時瞬間沉默了20秒，然後奶奶眼眶紅紅地告訴我「對不起」。</p>
        <p><br></p>
        <p class="hash_tag">看了好心疼</p>
        <p class="hash_tag">我們能做的就是多陪伴<img class="emoImg" src="@/../static/emote/1f62d.png"><img class="emoImg" src="@/../static/emote/1f62d.png"><img src="@/../static/emote/1f62d.png"></p>
        <p><br></p>
        <p><br></p>
      </div>
      <div class="lineWrapper forcePaddingZero">
        <TweenVideo :src="TweenVideoSrc[3]"></TweenVideo>
      </div>
      <div class="lineWrapper gickBg">
        <ReadEnd></ReadEnd>
        <p><br></p>
        <p>子女離巢的核心家庭，不少長輩選擇搬進老人公寓，少了家人的陪伴，內心難免孤寂。但是透過青銀共居，促成長輩與年輕人跨代生命經驗交流，幫助長者走出孤獨。</p>
        <p><br></p>
        <p>陽明老人公寓社工師謝佳君說，有了這些年輕人的陪伴，可以讓長輩有更開闊的心胸，接受不同領域的新事物，發掘自己生命中更多的可能性，不再為家庭的事往心裡去。「讓老人家有走出去的機會，這就是青銀共居的目的。」</p>
        <p><br></p>
        <p>同住在一個屋簷下的長輩和年輕人，抽離血緣關係，與其說像家人，更像是「鄰居以上，家人未滿」的關係，平常有各自的生活空間，又能不時互相關照陪伴。</p>
        <p><br></p>
        <p>老人公寓走廊上迴盪著年輕笑聲，為長者的生活增添幾許活力與溫暖，更讓我們看見血緣之外，不同世代也可以有很美好的互動。</p>
      </div>
    </ContentContainer>
    <ContentContainer style="background-color: #fff">
      <Share href="https://udn.com/upf/newmedia/2018_data/cohousing/index.html"></Share>
      <Logo>
        <div class="logo">
          <a href="https://vision.udn.com/" target="_blank"><img src="https://udn.com/upf/newmedia/img/logo_udnhope2.jpg"></a>
        </div>
      </Logo>
      <p><br></p>
      <Question href="https://www.surveycake.com/s/KpQKN"></Question>
      <p><br></p>
      <Banner
        src_1="@/../static/image_0812/img_11.jpg"
        src_2="@/../static/image_0812/img_12.jpg">
      </Banner>
      <p><br></p>
      <Editor>
        <div>文字：蔡佩蓉、章凱閎、游昊耘</div>
        <div>影音：張心慈、王騰毅</div>
        <div>攝影：王騰毅</div>
        <div>視覺設計：張心慈</div>
        <div>網頁製作：廖克樸</div>
        <div>監製：何振忠、梁玉芳、董谷音、潘如瑩、蔡幸怡</div>
        <div>2018.08.24</div>
      </Editor>
      <p><br></p>
      <Relate :jsonProps="RelateData"></Relate>
      <p><br></p>
      <FbComment href="https://udn.com/upf/newmedia/2018_data/cohousing/index.html"></FbComment>
    </ContentContainer>
  </div>
</template>

<script>
import Banner from './components/Banner'
import Cover from './new_comp/Cover'
import ContentContainer from './new_comp/Content'
import Chat from './components/Chat'
import Carousel from './components/Carousel'
import Editor from './new_comp/Editor'
import FbComment from './new_comp/FBComment'
import FixLineList from './components/FixLineList'
import Headbar from './new_comp/HeadBar'
import Logo from './new_comp/Logo'
import Question from './new_comp/Question'
import ReadEnd from './components/ReadEnd'
import Indicator from './new_comp/Indicator'
import Relate from './new_comp/Relate'
import Share from './new_comp/Share'
import TweenVideo from './components/TweenVideo'

export default {
  name: 'App',
  components: {
    Banner,
    Carousel,
    Chat,
    Cover,
    ContentContainer,
    Editor,
    FbComment,
    FixLineList,
    Headbar,
    Logo,
    Question,
    ReadEnd,
    Indicator,
    Relate,
    Share,
    TweenVideo
  },
  data () {
    return {
      introShow: false,
      TweenVideoSrc: [
        '@/../static/video_0812/video_1.mp4',
        '@/../static/video_0812/video_2.mp4',
        '@/../static/video_0812/video_3.mp4',
        '@/../static/video_0812/video_4.mp4'
      ],
      MeiAnCarouselMenu: [
        {
          id: "img_1",
          img: "@/../static/image_0812/img_1.jpg",
          info: "我和室友育甄常到安娜奶奶的房間閒聊、吃點心，奶奶說，跟年輕人聊天最開心了。",
          isActive: true
        },
        {
          id: "img_2",
          img: "@/../static/image_0812/img_2.jpg",
          info: "我和室友育甄常到安娜奶奶的房間閒聊、吃點心，奶奶說，跟年輕人聊天最開心了。",
          isActive: false
        },
        {
          id: "img_3",
          img: "@/../static/image_0812/img_3.jpg",
          info: "100歲的陳端和爺爺，在陽明老人公寓已經住了20年。他最大的興趣是寫書法，牆上掛的就是他的作品。",
          isActive: false
        }
      ],
      AnnaCarouselMenu: [
        {
          id: "img_4",
          img: "@/../static/image_0812/img_4.jpg",
          info: "已經有兩年的復活節，我教大家做彩蛋，蛋很可愛，彩色蛋尤其漂亮，每個人都喜歡。",
          isActive: true
        },
        {
          id: "img_5",
          img: "@/../static/image_0812/img_5.jpg",
          info: "兩個月前，莉君剛畢業，她穿著學士服來跟我道別。和她相聚時間短暫，到現在心裡還是很捨不得她。圖／劉莉君提供",
          isActive: false
        }
      ],
      SterCarouselMenu: [
        {
          id: "img_6",
          img: "@/../static/image_0812/img_6.jpg",
          info: "我們每個月必須完成20小時的服務時數，陪爺爺奶奶打麻將、玩桌遊等。圖／陽明老人公寓提供",
          isActive: true
        },
        {
          id: "img_7",
          img: "@/../static/image_0812/img_7.jpg",
          info: "我們每個月必須完成20小時的服務時數，陪爺爺奶奶打麻將、玩桌遊等。圖／陽明老人公寓提供",
          isActive: false
        },
        {
          id: "img_8",
          img: "@/../static/image_0812/img_8.jpg",
          info: "我試著將20小時的陪伴服務轉化成一種反射動作，跟長輩由心出發的交流。",
          isActive: false
        }
      ],
      YuiChenCarouselMenu: [
        {
          id: "img_9",
          img: "@/../static/image_0812/img_9.jpg",
          info: "和公寓的長輩互動，可以感受到他們真誠的關心，我很珍惜這樣的情感交流。",
          isActive: true
        },
        {
          id: "img_10",
          img: "@/../static/image_0812/img_10.jpg",
          info: "和公寓的長輩互動，可以感受到他們真誠的關心，我很珍惜這樣的情感交流。",
          isActive: false
        }
      ],
      RelateData: {
        title: '延伸閱讀',
        href1: 'https://ubrand.udn.com/ubrand/story/11817/3271495?issue=01',
        text1: '拒絕蝸居台北 玖樓給青年租得起的好生活',
        img1: '@/../static/image_0812/read1.jpg',
        href2: 'https://vision.udn.com/vision/story/12184/3250141',
        text2: '聽銀髮族搖滾說故事 「搖滾爺奶」開啟對老年的想像',
        img2: '@/../static/image_0812/read2.jpg',
        href3: 'https://vision.udn.com/vision/story/12329/3240424',
        text3: '當兩代理髮師相遇 老師傅頂上功夫他看得入迷',
        img3: '@/../static/image_0812/read3.jpg',
        href4: 'https://ubrand.udn.com/ubrand/story/11816/3225864?issue=01',
        text4: '跨世代友誼 不能告訴爸媽的都和這些老人說',
        img4: '@/../static/image_0812/read4.jpg'
      }
    }
  },
  methods: {
    handle_scroll (target) {
      let currentH = window.pageYOffset
      if ((currentH > $(this.$refs.introSec).offset().top - window.innerHeight * 0.8) && !this.introShow) {
        console.log('true it')
        this.introShow = true
      }
    }
  },
  mounted () {
    window.addEventListener('scroll', this.handle_scroll)
  }
}
</script>

<style lang="scss">
.cus_cover_bg{
  background-position: top center !important;
  padding-bottom: 5% !important;
}
.cus_cover_title{
  padding: 10px;
  background-color: #f0f2f2;
}
.timeline{
  position: fixed;
  z-index: 20;
  width: 100%;
  height: 100vh;
  background-color: #f0f2f2;
  pointer-events: none;
  hr{
    position: absolute;
    left: 50%;
    top: 0;
    margin-left: -1px;
    border-top: none;
    border-left: .5px solid #bcbbbb;
    border-right: .5px solid #bcbbbb;
    height: 66%;
  }
}
.lineWrapper{
  position: relative;
  width: 100%;
  padding: 20px 15px;
  background-color: #fff;
  p:last-child{
    margin-bottom: 0;
  }
  @media screen and (min-width: 1025px) {
    max-width: 600px;
  }
}
.lineHead{
  position: relative;
  width: 100%;
  display: flex;
  align-items: center;
}
.line_profile{
  width: 70px;
  height: 70px;
  border-radius: 50%;
  display: flex;
  align-items: center;
  justify-content: center;
  margin-right: 10px;
  img{
    width: 80%;
  }
}
.line_title{
  h4{
    font-weight: bold;
    margin: 0;
  }
  span{
    font-size: 12px;
    letter-spacing: 0.6px;
    text-align: left;
    color: #7b7b7b;
    line-height: 2.67;
  }
}
.hash_tag{
  color: #365899;
  font-size: 16px;
  line-height: 1.75;
  &::before{
    content: '#'
  }
}
.forcePaddingZero{
  padding: 0 !important;
}
.forceContentPaddingZero{
  @media screen and (max-width: 1025px) {
    padding: 0 !important;
  }
}
.gickBg{
  background-color: #fff;
  @media screen and (min-width: 1024px) {
    background-color: #f0f2f2;
  }
}
.animated{
  opacity: 0;
}
.emoImg{
  margin-right: 2px;
}
</style>
