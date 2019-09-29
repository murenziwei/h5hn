<template>
  <div class="out-div" v-show="active>=0">
    <div class="lw-fixed">
        <ul class="lw-tabbar">
            <li class="lt-item" v-for="(val,ind) of list" :key="ind">
                <router-link :to="val.path" class="li-nav" replace>

                    <img class="li-icon" :src="(active===ind?val.selIcon:val.icon)" alt="">
                    <div :class="{'li-text':true,'active':active===ind}">
                        {{val.text}}
                    </div>
                </router-link>
            </li>
        </ul>
    </div>
  </div>
</template>

<script>
export default {
    name:'tabbar',
    data() {
        return {
            active:-1,
            list:[
                {
                    path:'/',
                    icon:'data:image/png;base64,iVBORw0KGgoAAAANSUhEUgAAADoAAAA6CAYAAADhu0ooAAAJKUlEQVRoQ+1aa3CU5RV+nnc3WZLsBoriBUMSKlasba2Fom1HUWurqAhTS3RQS8VGsvlhZyohqNOZnc4UCXHs1GmzCaHQQqUtaBVU0GkrqNOKFsfSi1pRExKNFyhIdjeXvXxP59uQTCB7+TbBkFb2VybfuT3vOe95z3vOS3xCfvyE4MRJoP9vnj7p0ZMeHcYKzNkmj8cXqzBilciLIO0S2Ngbdm3efg17hyEyZ5aPNXTnPts9FXAvIbAY0KSh1nG/LKyFiTc9PrugJWfrc2A4/kADMldfmrjahUQ1gasBuLLaI1gitgMKPvmcZzsCtLLy5Ehw3IBetkOnemLdi0FWAZiaox2DyNkCscnEo2u3X+PbP3w5R3OOGOiV27ouhmE1DRZAGne8DAPQK+BhC2h45qrCv4xU7rCAznhcheNNz0LQqgZw4UiNyMov7JFxNSjUuXFnxWnhrPQpCHIC+rXtPee6rLifwiIAE4ajcEQ8xGFZ3KCEFXx+vu/VXGRlBXpZYIc7duHM6ylUg7iCGANlIyEBzyqBYM+H3kdfXsJYNtBpgc54JHKmm/FKQ1MJqCSboBP3ne9ZsNbAylv94g2F76SzYwjQmZsPXUawmuB8AHknDkCOmom4xMclK7i7YvwfAWqwhCTQadvkKe48VEnSD/KzOaoYc+QU3rCgRg8nNL5QwW7bwCTQL/7m4GMQ5o05i0du0JN/WzjxugGgX3joYC+k/JHLHWMSyOjfb57oGQB63oYDT9PCN8eYmcfBHG1/ddGkawaAnr/pQ28igjsFLgFUehw0nFARIt+irKZQ9LSfdyxh1wDQAas2yTUtdOBaQH7I9rDMCbU4F+VkAsQ2CcG3Fk96CkyRdVPJm9L0wdluokrUbRBOyUXnaNIS2C9j1iCWWN3qP7PV8Tl6LGH5upZxVve4G2Vgl34XjSaIjLrIP1NWcF8s8jDuPCfr5T1rCThY2eSfdXwJVDXAmwAVjT5ohklshLEa3q0q2ZOL/pyA9gue8JOWCR63Z5EkP6Fzc1E4LFryNQDBaKRn/aHlZx8ejowjQEVv/TuzZVmuyO4Xd2JzRcKZMPGUn7ZdARk7ec0D4XbG54gqBmILwYYD3y/Z4YjDJlqwyeWdNWs2LChcW7azvxRMAvWtav0FycVHhLVb0mrFCpoj957+gVMFBQ+0n+WRVQmwUsBkp3zH0pF4F1RzNMrmrtrSDqdyin789unMN98zMHf0H5GS1oaWld8+cLz4Vu2L8RhvCIhSeNQybAgvLX3OqUIE5B7vbZtvSX6AlwNysD3so0A7jEHD4VDZFgQYd6rPu/LtS43L+AV+i8BR1Z2AWKimLPm/Po/Wt+4imDajCvinyGA4UbABtZNCTo3IX9EyPY/wy+A7UIqLOvkRofWxBILRe6a+7lQu6vb7vK7uW5nMEfhcOj5Ju0LLyr8yALRoVcsZLrp+CFi3AvRlUBgC+OtEgsHI8in/cGxYoKMwz9OzkGIVoRkCXpFBMHYgtBH3XxBxKqdoZfvnXSbhB3FLZjsVAsyGRDT+o8i9n05uv6PDqu51n9c17laKGVfKZhTwvCUGI12hRxA4P+rU2L5QPrpqycgb+Fd+UWHhDYbGtumSTLR9kadgONGzAbXTj4q8tPvHt6rtEtKqThX7g5UJ+hDEmng8v6l7+eQ254AzUxas7Ch1m+gSGN5O4fT04Ykoqd9LpiG0rPT5dHRZE0WqbJZKmIAEhCcJK9hZU/70sbWmowWQWFzfepVg7PC8lpma32KbRWu1otaa/vDMpCMr0AHmBZtcvllfvo5w+QV8g5kKfuEtQY2Iu9eF7in5TzaQvhWvnQJ3wW0Eq0CcndZ7oEXgD0IiGHrpr084P++H2dErfqB9muKqol3wAxPTG4ZugJtosaGzdspLx9IV17XPkkn2hisIFGRYkIMS1zHBxs67p7yZbeFSfe/zaP2eIi8m3ALR0Lg3h5ZOPuBI2APtBb64biTgBzUrC8/LgoJg/hYoOo+gH8CMjDziSwKCITd/hx9MSfZ+sv18gX+fqsKCBTZdmIfWo6YvqyeBFte3bQM0x/5bQA+AzfbAJ1RT/kI2wf3fC+vaZrpc9g1HNwEodMqXgq5L5G8TCQS7akt3O5VTXNdysYyxo2MBgb7RiPRU57LyJK4jBUNbnFCqqdcryRXFRxv7Vyab4vH37fuUXPyuCPvM/Ew2+v7vAt+g0MiEfnn47rJDjvgCHYU+b2IhlbBvVENGI3aCDNWUJevvI0D3bSUwN4PwjyxgPWkFQ0udVjBi0f1tVxolQ3QuoSEFv8A4ZD1hl5mRpaVDerHp7PGtaJkul/Ebu+LKMBoRsTW0tCzZ3ezbo4GWccVFpkqwSypm8oI9Cthhn1nhrhLHNWlB3Tsleca6Q1AlgTMEvE+wOWaizd13TWt35j25vYX75pGwm+uXDyl2BgkR9AbFhs4uqwmBqfZWPHaOIhbVt33dSNUg5xLpr10COmihOQ6udnzLCOxwF3umlXf2lrQ6LdwL69omu43sG5G9SGelWxQBcYBbLSgYqSn9U8pOfSrmgrq9JXnMrxSTCs7MoCAGYauohnBN+TOOvOOAyFvfekXfYIvXM8NoRMB7FJpjijZ3157jfPYyxIY7dud5p02aT8oOmdmZQwav28krnPD9Cssn5t4JWHlwvNcVWsS+LTQ9w3pIxE5ZCIbf3P8YVs8c/jQtlRJvXet5xkW7m2AngfEZDIkI2JgwCnbdVf5KNgcW3td6ocudvEgsBJCpF3UYxHoroWC4ttxurzj+OS8BB4usf7/Ix96boaSXL8ioTdoFOzEURDcd1a17cK+nuDu/ItldBJJ3xvTbQ3tANoTkeQg1Zzi+1g2WNzyggyT4VrZ+VQbVJL5NMDnnSPM7IGItqC0Q51H2kxycmgFcr4SHaaEhtLz8xLxhSBnWK/ZOYl7+YgJLRvYqBS0CmhSLrg3fc87YeZUyBHRAprho3xyA9i1nDoGsYw0BFqWnQDR0RsrG9jujVF4eV986NS85uOJipng5JnA/pHUxqrGnpvx/7OVYKsQP7vUU9eYvMID92MpOPC9YMI0RT89mJ+MEx6k1A+GIk9HxMGI0ZJwEOhqrPJo6Tnp0NFd7NHSd9OhorPJo6vgv8k+LaOqHWPMAAAAASUVORK5CYII=',
                    selIcon:'data:image/png;base64,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',
                    text:'首页'
                },
                {
                    path:'/about',
                    icon:'data:image/png;base64,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',
                    selIcon:'data:image/png;base64,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',
                    text:'我的'
                }
            ]
        }
    },
    created(){
        this.routerfn(this.$route)
    },
    methods:{
        routerfn:function(to){
            switch (to.path) {
                case "/":this.active=0;break;
                case "/about":this.active=1;break;
                default:this.active=-1;
            }
        }
    },
    watch:{
        '$route':'routerfn'
    }
}
</script>

<style scoped lang="less">
   ul,li{
       padding:0;
       margin:0;
   }
   .out-div{
       height:50px;
   }
   .li-nav{
        display:flex;
        height:50px;
        align-items:center;
        justify-content: center;
        flex-direction: column;
        width:100%;
        text-decoration:none;
   }
   .lw-fixed{
       position:fixed;
       bottom:0;
       left:0;
       right:0;
       .lw-tabbar{
           display:flex;
           .lt-item{
               flex:1;
               display:flex;
               height:50px;
               align-items:center;
               justify-content: center;
               flex-direction: column;
               .li-icon{
                   width:29px;
                   height:29px;
               }
               .li-text{
                   color:#A8ABAF;
                   font-size:11px;
                   font-family:Source Han Sans CN;
                   font-weight:400;
                   &.active{
                    color:#0D83DD;
                   }
               }
               &:active{
                   opacity:.7;
               }
           }
       }
   }
</style>