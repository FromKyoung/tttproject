<template>
    <div>
        <div>
            <div class="container">
        <div class="left">
            <h2>지도 선택</h2>
            <img :src="image" :usemap="'#' + mapName" @load="onImageLoad" />
            <map name="map">
                <area v-for="(area, index) in scaledAreas"
                :key="index"
                :shape="area.shape"
                :coords="area.coords.join(',')"
                @click.prevent="navigateTo(area.routePath)"
                />

                <!-- <area shape="poly" :coords="[172,196,167,204,170,208,175,211,173,218,177,222,181,217,189,231,193,226,198,229,203,223,207,227,208,225,212,230,219,226,230,219,226,216,230,208,237,207,242,205,234,199,223,203,220,201,223,194,222,187,219,188,218,176,210,177,206,175,202,182,200,189,195,185,193,187,190,185,189,192,182,199]" alt="서울" @click.prevent="navigateTo('/region/seoul')"> -->

                <!-- <area class="area2" alt="강원" shape="poly" href="region/gangwon/gangwon_main.html" coords="410,36,395,48,377,49,349,72,312,71,296,79,273,80,260,77,245,77,231,74,219,85,229,100,239,103,239,108,263,114,265,123,273,128,276,136,288,139,297,152,297,161,281,161,276,167,279,190,296,195,300,200,315,204,319,208,312,216,314,222,305,271,315,280,329,276,342,262,344,269,353,272,370,262,401,268,394,271,399,277,406,276,411,284,417,282,425,287,445,292,456,297,461,288,476,291,483,285,494,294,506,289,523,295,531,280,551,273,547,262,533,239,530,226,500,187,462,146,433,100,434,86"  >
                <area class="area2" alt="경기1" shape="poly" href="region/gyeonggi/gyeonggi_main.html" coords="219,86,199,105,182,110,161,112,154,122,152,148,153,158,160,188,168,198,154,193,148,172,132,177,133,190,137,204,146,209,155,203,167,203,175,196,181,198,188,194,190,184,198,184,201,189,206,174,219,177,220,183,222,190,222,203,241,197,283,192,277,164,285,159,298,160,297,149,289,138,278,137,276,127,265,123,264,114,240,106,241,103,231,100"  >
                <area class="area2" alt="경기2" shape="poly" href="region/gyeonggi/gyeonggi_main.html" coords="166,206,166,218,180,234,162,241,160,249,164,255,172,251,176,256,164,272,157,265,150,267,151,283,157,286,162,279,171,280,170,286,164,290,165,296,163,301,168,307,169,301,176,301,178,297,181,301,174,310,174,315,181,321,197,323,208,321,220,315,232,319,239,325,249,323,268,300,282,298,287,291,287,285,305,276,315,226,313,218,319,211,315,205,300,202,296,195,281,192,237,199,242,204,233,207,228,214,231,217,221,224,213,231,210,224,203,225,197,230,193,227,190,230,182,217,177,222,173,216,176,208"  >
                <area shape="poly" :coords="[172,196,167,204,170,208,175,211,173,218,177,222,181,217,189,231,193,226,198,229,203,223,207,227,208,225,212,230,219,226,230,219,226,216,230,208,237,207,242,205,234,199,223,203,220,201,223,194,222,187,219,188,218,176,210,177,206,175,202,182,200,189,195,185,193,187,190,185,189,192,182,199]" alt="서울" @click.prevent="navigateTo('/region/seoul')">
                <area class="area4" alt="인천" shape="poly" href="" coords="86,166,93,160,101,162,107,169,119,161,123,164,131,176,133,193,137,204,146,209,155,203,166,203,166,218,180,232,163,240,166,231,158,233,153,236,148,229,140,231,138,223,150,222,148,210,134,202,128,198,123,205,110,204,98,191,93,182,93,174,84,172,86,166" >
                <area class="area5" alt="대전" shape="poly" href="" coords="253,398,238,411,236,435,246,448,260,447,279,419,271,410,269,404" >
                <area class="area5" alt="세종" shape="poly" href="" coords="243,358,239,379,250,390,254,398,239,410,231,411,220,389,224,383,216,376,215,362,222,355"  >
                <area class="area5" alt="충북" shape="poly" href="" coords="272,431,292,474,305,484,320,482,329,485,349,456,347,445,337,440,328,444,329,421,325,406,328,389,316,383,326,372,335,374,333,363,337,358,351,359,359,358,352,353,353,343,373,341,385,334,398,341,411,338,410,320,425,312,443,292,426,289,418,284,410,286,405,278,398,279,392,272,398,269,370,264,352,272,345,270,342,262,330,276,315,282,307,274,289,283,288,291,282,297,269,298,250,318,241,323,243,332,253,334,254,342,260,348,244,357,241,380,255,400,269,405,272,409,279,417,269,405" >
                <area class="area5" alt="충남" shape="poly" href="" coords="272,431,292,472,286,487,267,493,256,483,248,468,228,470,211,477,205,463,188,462,181,471,176,469,166,480,145,489,140,475,124,463,124,435,122,419,120,403,116,374,93,381,87,363,75,364,72,344,79,336,81,328,89,326,93,314,98,329,95,337,101,342,102,332,112,324,104,318,106,311,117,308,124,319,124,303,133,300,143,314,152,312,155,317,161,313,168,328,172,345,177,339,176,332,179,327,197,328,196,321,207,321,220,315,232,319,240,326,243,332,253,336,253,342,260,350,243,358,222,356,214,362,215,375,224,382,221,389,231,410,238,409,235,434,244,447,260,447" >
                <area class="area6" alt="경북" shape="poly" href="" coords="566,551,545,543,537,545,524,539,514,540,496,553,462,560,436,564,433,551,441,533,455,531,468,506,452,489,434,495,419,516,427,523,422,539,413,540,412,555,404,555,375,548,371,535,372,524,362,516,352,520,336,513,330,504,330,485,349,454,348,444,339,439,329,440,329,417,325,405,329,388,317,381,327,370,336,374,334,361,339,356,352,362,357,357,353,351,354,342,375,340,385,334,398,342,412,339,411,321,425,312,443,290,448,296,456,298,462,290,475,292,484,288,493,296,503,291,514,293,522,297,532,281,551,272,557,280,556,304,561,307,560,326,565,335,564,359,561,371,564,392,557,416,558,433,553,446,559,455,560,465,552,471,552,477,562,480,574,468,581,469,580,481,576,488,578,516,568,531" >
                <area class="area6" alt="전북" shape="poly" href="" coords="189,462,176,476,170,486,157,493,143,492,135,500,140,505,154,509,163,505,170,505,155,515,160,527,140,527,137,536,116,552,117,563,132,564,123,574,109,589,114,599,136,615,155,598,161,587,176,587,180,592,193,595,196,587,202,588,197,608,209,612,224,609,253,611,259,602,269,604,281,611,287,599,292,596,293,590,290,584,286,554,302,532,330,505,328,484,320,481,306,485,292,474,287,486,268,493,257,484,247,468,229,469,224,473,212,476,205,464" >
                <area class="area7" alt="대구" shape="poly" href="" coords="433,553,414,557,413,543,421,540,427,523,419,517,431,498,451,490,466,505,466,513,455,531,442,533"  >
                <area class="area7" alt="경남" shape="poly" href="" coords="328,507,300,535,287,555,290,584,294,592,294,598,287,600,281,614,287,626,294,640,297,647,308,662,311,673,316,669,320,678,318,695,323,720,333,714,338,721,350,720,356,706,354,691,346,686,340,692,331,670,336,674,345,674,343,662,351,668,352,678,366,689,375,704,379,704,377,690,385,685,391,694,400,695,407,700,402,705,410,713,422,715,432,701,437,725,451,717,455,703,455,687,451,674,458,667,468,669,474,658,482,651,490,640,490,631,495,615,522,603,528,582,514,579,512,571,498,569,495,555,467,558,464,563,454,562,437,564,432,553,404,558,386,552,374,550,371,539,372,526,360,518,352,523,336,516" >
                <area class="area7" alt="울산" shape="poly" href="" coords="497,556,497,568,515,572,528,582,541,594,551,596,552,584,550,575,558,579,567,569,568,557,565,550,544,543,537,547,523,540,513,539"  >
                <area class="area8" alt="전남1" shape="poly" href="" coords="143,627,147,640,155,649,184,650,202,636,197,622,208,614,223,609,253,611,258,603,269,604,282,612,286,625,294,639,297,647,309,661,310,675,298,684,288,682,285,687,288,699,300,697,305,694,312,697,309,702,311,717,303,719,296,713,290,718,290,735,284,732,278,734,276,723,285,715,279,711,277,701,275,690,271,687,269,693,255,702,254,709,250,717,265,728,269,737,264,743,251,736,250,744,257,747,253,755,246,756,247,764,243,768,236,757,228,772,213,771,209,763,211,748,217,743,219,737,231,736,230,721,241,727,244,717,234,714,231,705,224,707,224,715,202,734,194,731,192,746,184,753,182,764,188,778,179,788,158,796,132,786,119,789,117,775,116,757,124,741,104,750,86,743,83,712,91,712,97,733,104,722,104,710,93,696,77,697,87,684,88,673,100,666,88,659,81,660,75,647,78,640,93,639,94,623">
                <area class="area6" alt="전남2" shape="poly" href="" coords="95,622,101,611,100,603,106,603,114,609,114,599,136,615,153,600,161,587,174,586,180,593,192,595,196,589,202,589,198,607,209,612,195,622,172,617,144,627" >
                <area class="area9" alt="부산" shape="poly" href="" coords="528,583,522,597,522,602,495,615,489,631,490,640,487,653,492,658,501,654,510,655,519,638,530,638,533,621,550,596,541,594" >
                <area class="area10" alt="광주" shape="poly" id="광주" href="" coords="144,626,148,648,164,644,184,652,199,634,196,622,177,618" >
                <area class="area11" alt="제주" shape="poly" id="jeju" href="" coords="85,896,70,903,72,916,91,932,108,921,129,929,145,925,150,918,171,918,189,906,192,892,197,888,185,870,161,866,151,872,126,871,123,881,105,878,101,884,89,883,86,890" > -->
            </map>
        </div>
        <div class="line"></div>
        <div class="right">
            <h2>지역 선택</h2>
            <div class="button-container">
                <div class="button-row">
                    <div class="button"><router-link to="/region/seoul"><div class="button">서울</div></router-link></div>
                    <div class="button"><router-link to="/region/gyeonggido"><div class="button">경기</div></router-link></div>
                    <div class="button"><router-link to="/region/incheon"><div class="button">인천</div></router-link></div>
                </div>
                <div class="button-row">
                    <div class="button"><router-link to="/region/gangwondo"><div class="button">강원</div></router-link></div>
                    <div class="button"><router-link to="/region/chungcheongnamdo"><div class="button">충남</div></router-link></div>
                    <div class="button"><router-link to="/region/chungcheongbukdo"><div class="button">충북</div></router-link></div>
                </div>
                <div class="button-row">
                    <div class="button"><router-link to="/region/sejong"><div class="button">세종</div></router-link></div>
                    <div class="button"><router-link to="/region/daejeon"><div class="button">대전</div></router-link></div>
                    <div class="button"><router-link to="/region/gyeongsangbukdo"><div class="button">경북</div></router-link></div>
                </div>
                <div class="button-row">
                    <div class="button"><router-link to="/region/ulsan"><div class="button">울산</div></router-link></div>
                    <div class="button"><router-link to="/region/daegu"><div class="button">대구</div></router-link></div>
                    <div class="button"><router-link to="/region/gyeongsangnamdo"><div class="button">경남</div></router-link></div>
                </div>
                <div class="button-row">
                    <div class="button"><router-link to="/region/busan"><div class="button">부산</div></router-link></div>
                    <div class="button"><router-link to="/region/jeollabukdo"><div class="button">전북</div></router-link></div>
                    <div class="button"><router-link to="/region/jeollanamdo"><div class="button">전남</div></router-link></div>
                </div>
                <div class="button-row">
                    <div class="button"><router-link to="/region/gwangju"><div class="button">광주</div></router-link></div>
                    <div class="button"><router-link to="/region/jejudo"><div class="button">제주</div></router-link></div>
                    <div class="button"><router-link to=""><div class="button">관심지역</div></router-link></div>
                </div>
            </div>
        </div>
    </div>
    <!-- <aside>
        <div class="sidebar">
            <h2>추천해요</h2>
            <div class="circle-container">
                <div class="circle">
                    <img src="" alt="image">
                </div>
                <div class="circle">
                    <img src="" alt="image">
                </div>
                <div class="circle">
                    <img src="" alt="image">
                </div>
            </div>
        </div>
    </aside> -->
            
        </div>
    </div>
</template>

<script>
export default {
    data() {
    return {
      image: require('../assets/main_map.png'),
      mapName: 'map',
      areas: [
        {//서울
          shape: 'poly',
          coords: [172,196,167,204,170,208,175,211,173,218,177,222,181,217,189,231,193,226,198,229,203,223,207,227,208,225,212,230,219,226,230,219,226,216,230,208,237,207,242,205,234,199,223,203,220,201,223,194,222,187,219,188,218,176,210,177,206,175,202,182,200,189,195,185,193,187,190,185,189,192,182,199],
          routePath: '/region/seoul',
        }, 
        {//강원
            shape: 'poly',
            coords: [410,36,395,48,377,49,349,72,312,71,296,79,273,80,260,77,245,77,231,74,219,85,229,100,239,103,239,108,263,114,265,123,273,128,276,136,288,139,297,152,297,161,281,161,276,167,279,190,296,195,300,200,315,204,319,208,312,216,314,222,305,271,315,280,329,276,342,262,344,269,353,272,370,262,401,268,394,271,399,277,406,276,411,284,417,282,425,287,445,292,456,297,461,288,476,291,483,285,494,294,506,289,523,295,531,280,551,273,547,262,533,239,530,226,500,187,462,146,433,100,434,86], 
            routePath: '/region/gangwondo',
        },
        {//경기1
            shape: 'poly',
            coords: [219,86,199,105,182,110,161,112,154,122,152,148,153,158,160,188,168,198,154,193,148,172,132,177,133,190,137,204,146,209,155,203,167,203,175,196,181,198,188,194,190,184,198,184,201,189,206,174,219,177,220,183,222,190,222,203,241,197,283,192,277,164,285,159,298,160,297,149,289,138,278,137,276,127,265,123,264,114,240,106,241,103,231,100], 
            routePath: '/region/gyeonggido',
        },
        {//경기2
            shape: 'poly',
            coords: [166,206,166,218,180,234,162,241,160,249,164,255,172,251,176,256,164,272,157,265,150,267,151,283,157,286,162,279,171,280,170,286,164,290,165,296,163,301,168,307,169,301,176,301,178,297,181,301,174,310,174,315,181,321,197,323,208,321,220,315,232,319,239,325,249,323,268,300,282,298,287,291,287,285,305,276,315,226,313,218,319,211,315,205,300,202,296,195,281,192,237,199,242,204,233,207,228,214,231,217,221,224,213,231,210,224,203,225,197,230,193,227,190,230,182,217,177,222,173,216,176,208], 
            routePath: '/region/gyeonggido',
        },
        {//인천
            shape: 'poly',
            coords: [86,166,93,160,101,162,107,169,119,161,123,164,131,176,133,193,137,204,146,209,155,203,166,203,166,218,180,232,163,240,166,231,158,233,153,236,148,229,140,231,138,223,150,222,148,210,134,202,128,198,123,205,110,204,98,191,93,182,93,174,84,172,86,166], 
            routePath: '/region/incheon',
        },
        {//대전
            shape: 'poly',
            coords: [253,398,238,411,236,435,246,448,260,447,279,419,271,410,269,404], 
            routePath: '/region/daejeon',
        },
        {//세종
            shape: 'poly',
            coords: [243,358,239,379,250,390,254,398,239,410,231,411,220,389,224,383,216,376,215,362,222,355], 
            routePath: '/region/sejong',
        },
        {//충북
            shape: 'poly',
            coords: [272,431,292,474,305,484,320,482,329,485,349,456,347,445,337,440,328,444,329,421,325,406,328,389,316,383,326,372,335,374,333,363,337,358,351,359,359,358,352,353,353,343,373,341,385,334,398,341,411,338,410,320,425,312,443,292,426,289,418,284,410,286,405,278,398,279,392,272,398,269,370,264,352,272,345,270,342,262,330,276,315,282,307,274,289,283,288,291,282,297,269,298,250,318,241,323,243,332,253,334,254,342,260,348,244,357,241,380,255,400,269,405,272,409,279,417,269,405], 
            routePath: '/region/chungcheongbukdo',
        },
        {//충남
            shape: 'poly',
            coords: [272,431,292,472,286,487,267,493,256,483,248,468,228,470,211,477,205,463,188,462,181,471,176,469,166,480,145,489,140,475,124,463,124,435,122,419,120,403,116,374,93,381,87,363,75,364,72,344,79,336,81,328,89,326,93,314,98,329,95,337,101,342,102,332,112,324,104,318,106,311,117,308,124,319,124,303,133,300,143,314,152,312,155,317,161,313,168,328,172,345,177,339,176,332,179,327,197,328,196,321,207,321,220,315,232,319,240,326,243,332,253,336,253,342,260,350,243,358,222,356,214,362,215,375,224,382,221,389,231,410,238,409,235,434,244,447,260,447], 
            routePath: '/region/chungcheongnamdo',
        },
        {//경북
            shape: 'poly',
            coords: [566,551,545,543,537,545,524,539,514,540,496,553,462,560,436,564,433,551,441,533,455,531,468,506,452,489,434,495,419,516,427,523,422,539,413,540,412,555,404,555,375,548,371,535,372,524,362,516,352,520,336,513,330,504,330,485,349,454,348,444,339,439,329,440,329,417,325,405,329,388,317,381,327,370,336,374,334,361,339,356,352,362,357,357,353,351,354,342,375,340,385,334,398,342,412,339,411,321,425,312,443,290,448,296,456,298,462,290,475,292,484,288,493,296,503,291,514,293,522,297,532,281,551,272,557,280,556,304,561,307,560,326,565,335,564,359,561,371,564,392,557,416,558,433,553,446,559,455,560,465,552,471,552,477,562,480,574,468,581,469,580,481,576,488,578,516,568,531], 
            routePath: '/region/gyeongsangbukdo',
        },
        {//전북
            shape: 'poly',
            coords: [189,462,176,476,170,486,157,493,143,492,135,500,140,505,154,509,163,505,170,505,155,515,160,527,140,527,137,536,116,552,117,563,132,564,123,574,109,589,114,599,136,615,155,598,161,587,176,587,180,592,193,595,196,587,202,588,197,608,209,612,224,609,253,611,259,602,269,604,281,611,287,599,292,596,293,590,290,584,286,554,302,532,330,505,328,484,320,481,306,485,292,474,287,486,268,493,257,484,247,468,229,469,224,473,212,476,205,464], 
            routePath: '/region/jeollabukdo',
        },
        {//대구
            shape: 'poly',
            coords: [433,553,414,557,413,543,421,540,427,523,419,517,431,498,451,490,466,505,466,513,455,531,442,533], 
            routePath: '/region/daegu',
        },
        {//경남
            shape: 'poly',
            coords: [328,507,300,535,287,555,290,584,294,592,294,598,287,600,281,614,287,626,294,640,297,647,308,662,311,673,316,669,320,678,318,695,323,720,333,714,338,721,350,720,356,706,354,691,346,686,340,692,331,670,336,674,345,674,343,662,351,668,352,678,366,689,375,704,379,704,377,690,385,685,391,694,400,695,407,700,402,705,410,713,422,715,432,701,437,725,451,717,455,703,455,687,451,674,458,667,468,669,474,658,482,651,490,640,490,631,495,615,522,603,528,582,514,579,512,571,498,569,495,555,467,558,464,563,454,562,437,564,432,553,404,558,386,552,374,550,371,539,372,526,360,518,352,523,336,516], 
            routePath: '/region/gyeongsangnamdo',
        },
        {//울산
            shape: 'poly',
            coords: [497,556,497,568,515,572,528,582,541,594,551,596,552,584,550,575,558,579,567,569,568,557,565,550,544,543,537,547,523,540,513,539], 
            routePath: '/region/ulsan',
        },
        { //전남1
            shape: 'poly',
            coords: [143,627,147,640,155,649,184,650,202,636,197,622,208,614,223,609,253,611,258,603,269,604,282,612,286,625,294,639,297,647,309,661,310,675,298,684,288,682,285,687,288,699,300,697,305,694,312,697,309,702,311,717,303,719,296,713,290,718,290,735,284,732,278,734,276,723,285,715,279,711,277,701,275,690,271,687,269,693,255,702,254,709,250,717,265,728,269,737,264,743,251,736,250,744,257,747,253,755,246,756,247,764,243,768,236,757,228,772,213,771,209,763,211,748,217,743,219,737,231,736,230,721,241,727,244,717,234,714,231,705,224,707,224,715,202,734,194,731,192,746,184,753,182,764,188,778,179,788,158,796,132,786,119,789,117,775,116,757,124,741,104,750,86,743,83,712,91,712,97,733,104,722,104,710,93,696,77,697,87,684,88,673,100,666,88,659,81,660,75,647,78,640,93,639,94,623],
            routePath: '/region/jeollanamdo',
        },
        {//전남2
            shape: 'poly',
            coords: [95,622,101,611,100,603,106,603,114,609,114,599,136,615,153,600,161,587,174,586,180,593,192,595,196,589,202,589,198,607,209,612,195,622,172,617,144,627], 
            routePath: '/region/jeollanamdo',
        },
        {//부산
            shape: 'poly',
            coords: [528,583,522,597,522,602,495,615,489,631,490,640,487,653,492,658,501,654,510,655,519,638,530,638,533,621,550,596,541,594], 
            routePath: '/region/busan',
        },
        {//광주
            shape: 'poly',
            coords: [144,626,148,648,164,644,184,652,199,634,196,622,177,618], 
            routePath: '/region/gwangju',
        },
        {//제주
            shape: 'poly',
            coords: [85,896,70,903,72,916,91,932,108,921,129,929,145,925,150,918,171,918,189,906,192,892,197,888,185,870,161,866,151,872,126,871,123,881,105,878,101,884,89,883,86,890], 
            routePath: '/region/jejudo',
        },
      ],
      scale: 1,
    };
  },
  computed: {
    scaledAreas() {
      return this.areas.map(area => ({
        ...area,
        coords: area.coords.map(coord => coord * this.scale),
      }));
    },
  },
  methods: {
    onImageLoad(event) {
        this.$nextTick(() => {
        this.updateScale(event);
        window.addEventListener('resize', this.updateScale);
  });
    },
    updateScale(event) {
      const naturalWidth = event.target.naturalWidth;
      const width = event.target.width;
      this.scale = width / naturalWidth;
    },
    navigateTo(href) {
      this.$router.push(href);
    },
  },
  beforeDestroy() {
    window.removeEventListener('resize', this.updateScale);
  },
};

</script>



<style>
body {
    margin: 0;
    padding: 0;
}

header {
    background-color: #fff;
    text-align: center;
}

h1 {
    margin: 0;
    padding: 20px 0;
    font-size: 60px;
    color: rgb(4,122,255); 
}

nav {
    background-color: #87CEFA;
}

nav ul {
    margin: 0;
    padding: 0;
    list-style: none;
    display: flex;
    justify-content: center;
}

nav li {
    margin: 0 10px;
}

nav a {
    display: block;
    padding: 10px;
    color: #fff;
    text-decoration: none;
}

nav a:hover {
    background-color: #fff;
    color: #87CEFA;
}

.container {
    display: flex;
    flex-direction: row;
    margin-top: 50px;
}

.left {
    flex: 1;
    height: 500px;
    background-color: #fff;
    padding: 20px;
    display: flex;
    flex-direction: column;
    align-items: center;
    justify-content: flex-start;
}

.left img {
    max-width: 100%;
    height: auto;
    margin-left: 100px;
}

img {
    width: 60%;
    height: auto;
}

map {
    display: block;
}

area {
    display: block;
    position: absolute;
}


/* .area {
    cursor: pointer;
} */

/*.area:hover {
    background-color: rgba(34, 0, 255, 0.5);
}*/

.right {
    flex: 1;
    height: 500px;
    background-color: #fff;
    padding: 20px;
    display: flex;
    flex-direction: column;
    align-items: center;
}

.line {
    width: 2px;
    background-color: #87CEFA;
    margin: 20px;
}

.button-container {
    margin-top: 20px;
    display: flex;
    flex-direction: column;
    align-items: center;
}

.button-row {
    display: flex;
    flex-direction: row;
}

.button {
    width: 100px;
    height: 50px;
    border-radius: 10%;
    background-color: #0077c2;
    margin: 20px;
    display: flex;
    justify-content: center;
    align-items: center;
    font-size: 14px;
    color: #fff;
    cursor: pointer;
}

.button a {
    font-size: 14px;
    color: #fff;
    text-decoration: none;
}

.button:hover {
    background-color: #ffffff;
    color: rgb(4,122,255);
}



.button a:hover {
    background-color: #ffffff;
    color: rgb(4,122,255);
}

aside {
    background-color: #F5F5F5;
    width: 110px;
    height: 550px;
    position: fixed;
    opacity: 70%;
    top: 60%;
    left: 0;
    transform: translateY(-50%);
    border-top-right-radius: 50px;
    border-bottom-right-radius: 50px;
    background-color: #87CEFA;
}

.sidebar {
    padding: 20px;
    display: flex;
    flex-direction: column;
    align-items: center;
}

h2 {
    margin: 0;
    font-size: 15px;
    text-align: center;
}

.circle-container {
    display: flex;
    flex-direction: column;
    align-items: center;
    margin-top: 30px;
}

.circle {
    width: 70px;
    height: 70px;
    border-radius: 50%;
    background-color: #fff;
    margin-top: 30px;
    margin-bottom: 40px;
    display: flex;
    justify-content: center;
    align-items: center;
}

.circle img {
    width: 60%;
    height: 60%;
    border-radius: 50%;
    cursor: pointer;
}

map {
    display: block;
    cursor: pointer;
}

</style>