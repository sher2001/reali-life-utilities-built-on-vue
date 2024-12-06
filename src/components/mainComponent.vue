<script setup>
import { ref } from 'vue'
import calculatorComp from './Calculator/calculatorComp.vue'
import formValidationAndPasswordgenerator from './Form validations and password generator/formValidationAndPasswordgenerator.vue'
import githubUserSearch from './Github user search/githubUserSearch.vue'
import randomGeneratorsWithpagenation from './Random generators with pagenation/randomGeneratorsWithpagenation.vue'
import todoComponent from './to-do/todoComponent.vue'
import wikiComponent from './Wiki clone/wikiComponent.vue'

const availablePages = {
  calculatorComp,
  formValidationAndPasswordgenerator,
  githubUserSearch,
  randomGeneratorsWithpagenation,
  todoComponent,
  wikiComponent,
}

const currentPage = ref('')
const isHomepage = ref(true)
const goToPage = (page) => {
  if (page === 'homePage') {
    isHomepage.value = true
    currentPage.value = ''
  } else {
    isHomepage.value = false
    currentPage.value = page
  }
}
</script>

<template>
  <div class="p-10 h-screen overflow-auto bg-slate-300">
    <!-- Page components -->
    <div class="w-full flex flex-col justify-between gap-4">
      <!-- backspace -->
      <div v-show="!isHomepage" @click="goToPage('homePage')" class="size-10 ui-button">
        <svg
          xmlns="http://www.w3.org/2000/svg"
          fill="none"
          viewBox="0 0 24 24"
          stroke-width="1.5"
          stroke="currentColor"
          class="size-6"
        >
          <path
            stroke-linecap="round"
            stroke-linejoin="round"
            d="M12 9.75 14.25 12m0 0 2.25 2.25M14.25 12l2.25-2.25M14.25 12 12 14.25m-2.58 4.92-6.374-6.375a1.125 1.125 0 0 1 0-1.59L9.42 4.83c.21-.211.497-.33.795-.33H19.5a2.25 2.25 0 0 1 2.25 2.25v10.5a2.25 2.25 0 0 1-2.25 2.25h-9.284c-.298 0-.585-.119-.795-.33Z"
          />
        </svg>
      </div>

      <div class="absolute right-24 w-fit ui-button">
        <a href="https://github.com/sher2001/reali-life-utilities-built-on-vue" target="_blank">
          <img
            class="rounded-full size-10"
            src="data:image/png;base64,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"
            alt="Source code"
          />
        </a>
      </div>

      <!-- Page Component -->
      <component :is="availablePages[currentPage]"> </component>
    </div>

    <!-- Menu components -->
    <div v-show="isHomepage" class="grid lg:grid-cols-3 gap-4 max-w-fit m-auto lg:py-40">
      <!-- left -->
      <div class="flex-center">
        <img
          @click="goToPage('todoComponent')"
          class="small-img lg:h-96 img-clickable"
          src="data:image/png;base64,iVBORw0KGgoAAAANSUhEUgAAAOEAAADhCAMAAAAJbSJIAAAAkFBMVEUdGyb///8AAAAaGCP39vcfHSkYFiIGABbn5ucVEyCNjJAMCBkAAAQxLzjIyMkTEB59fIAAAAsAABOHhorAv8EAAA/U1NXg4OH4+PgAABSlpadqaW5bWmBPTlTt7e1GRUwnJS+1tbd2dXk4Nj63triZmZtvbnJgX2SXl5rGxsg+PURVVFqsq66hoaQrKTPj4uS7F6LgAAAD+0lEQVR4nO3ZaXOqPACGYQgUtLghKGjdW083bf//v3srSkUgy5wB3zkz9/VRY8hjFkKwLAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAOAf4wz9SRiGk6DbQGVecKornA2dBiqrv4JQG5d/EIjZ4vEQxy+HaCl6w/LXzs2ve5NA1fJuKJ5H85c43u6fHOG3EtLr265KGoc35X2xG9i/0nghbjM6D3aa/zR1k8H8TyACWT7xcVhdK0se/Uk7CdUGvWJpMXJL3ycLUfzrfxKWTUf1GcPnQbnoUVTGxH0T+v2kpkQcFuZjTULbdkfCq1xYHOtKfvbKBe+ZMHyqL7LqX//52oQ//bgpdaPnT+srexT/X8Lwj6xMeo0oSWjbS/82YEdW2b7hiOYJg4W8kDvMR6E0ob0uTjFRN9wvotBqknFCz1KVmuZ/vDxh2r3ORfGiqmzd6HJjnFBI5s1FNNMlvP4L1vBVWdeq0XFqmlDTKNseO7qE9lPeN2IlL3QS+ZLWtplQNXEyb2NtwuTSN8FOU5fbZCcaJuyuNcXyoaVKaK/PN07NgLcLvX2/hJODrlH2sqtNOM92Zd5GW1fc4HJqmFB8a1v1NtMmPA/TINLW1eRao004PSV0fG2j7PeeNqGdNTzc6it7aPAxYxONTnbly6522eej19OU8D70jTp3kDrh5nRL1E9D2140eUsMMuKxdI2OOH+RXUp7r7DzkaVOmM1VId2wXe1kT1x/z68mLHw7lOy5i1KDhJ9Dw4Sjuyc06EP3n+5D/e0w/4E6Yd90Hr42/ySsTug4+kYNDBKe19JYX9lX5Ym55YTaneSP41ib8LzcVi5V1ei2zSxhqHzcyZwXeGXCQ7anMRjy742fZWgT6pca12BfernL6QdECwuNLqG+VceJNmFe5exNU1fawiDVJvR1m0lP/3yY3+ScmaaufeUY+g4JdZ24vxzmKhImvzWO1WtNG+uMQcLhUtWo39KKhP3rsar6ebrRTal5Qqunmj1f+rO218LRhPIRsenjROOElthKG7X8XfukCZ9uHmoD+R1j205Ak4SWmNe3KV1fu0eScLUuLR7+Oq2v7NBSQKOElqg9QkoeCnev+oTz6huXwKqdi7u2ApoltHyrsqd0o5u3LjUJ3bkT1jyyeyKqdGNsNXmOWGq7UcKfZn1si+1KInHbplLC1WC/FBPJNtoXUfH4J90+V19RNcjp3vIkJyXdUCyO70mn8z3dRl+i8p87z7/6G1+IsepVuC/60cv0u9NJ4v2nCNvMd2paibzkcNzLXmGHQV2TvCtVJXnpIDzXNW7lJggAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAD8nf8AuQo5iCJUvtUAAAAASUVORK5CYII="
          alt="To do list"
        />
      </div>
      <!-- center -->
      <div class="grid lg:grid-cols-2 gap-4">
        <div @click="goToPage('formValidationAndPasswordgenerator')" class="flex-center">
          <img
            class="small-img img-clickable"
            src="https://encrypted-tbn0.gstatic.com/images?q=tbn:ANd9GcR-Vzs2ytZ9AvoMWBcRsMSOzsIAYvDGH-nEdw&s"
            alt="Forms"
          />
        </div>
        <div @click="goToPage('randomGeneratorsWithpagenation')" class="flex-center">
          <img
            class="small-img lg:h-auto img-clickable"
            src="https://encrypted-tbn0.gstatic.com/images?q=tbn:ANd9GcTgRs2adEyOAEj-yiZeawK2QyMNabCduGjdTA&s"
            alt="generators"
          />
        </div>
      </div>
      <!-- Right -->
      <div class="grid lg:sgrid-cols-subgrid sm:grid-cols-1 gap-4">
        <div class="grid lg:grid-cols-2 sm:grid-cols-1 gap-4">
          <div @click="goToPage('wikiComponent')" class="flex-center">
            <img
              class="small-img lg:h-28 img-clickable"
              src="data:image/png;base64,iVBORw0KGgoAAAANSUhEUgAAAOEAAADhCAMAAAAJbSJIAAAAflBMVEUAAAD19fX9/f1vb2/4+Pj6+vrS0tJbW1t0dHSJiYnd3d3y8vLu7u4WFhZoaGjl5eWAgICZmZnExMQuLi7a2tqvr6/U1NS9vb0bGxuioqK2trbMzMxgYGBUVFTi4uKRkZEnJycODg48PDxMTExFRUU2NjapqamEhIQgICCWlpZ49tImAAAEwklEQVR4nO3cDVOqQBQGYPa0hxQQ0FASND9Kq///B+8uqNW9XQOWVnbmfWa61h2bOW/AAXZZPQ8AAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAABguCbxNC+DJEmCMp/Gk1uX07f18YmIWdaYiZ6O61sX1aNNQizFV5Ip2dy6sJ4s5T/xziHl8tbF9SAN6dt4NQrTWxdo6C2jn2Rvty7SREzT9f116ynFty6zu3eiux/fdEf0bqGWX3Ek0SihoKOFan7BXLWYZgkFzS3U07up7qENEwqaWqioZ6PqJNE0oaCRhZp6dWDRKqHgg4Wq+hTIlgnlk4WqejQ9Xcg0T+jYobhl0Tqh4O3vF9abvFPC3EJlPTlcLrbbJBTkTrMpuFNCdue8/3E72CqhkBZq60VKHROSKzeLfudt6Fuorg+Xo7BtQld205g6J3TkZnjZfRuyGyNTM4OEMwv1mUtk54QysVCfuVB0TihCC/UZe2SDhPRooUJTD2SS8MFChaaQ8G/uJdwaJdz+foHGdtIgodxZqNBYZJAwslCfuczgjJ9ZqM9cYXDVVlioz9zY4N5ibKE+c3uDhHsL9fUg6ppQutFoPG/OHRM6M9j23Hkk6tlCdb0IZKeEMrBQWz8+hhPbjXm7MpioRLJLQlf6jHbZiG0SurQJP47EFgkduWI7e+kwQ/pioa4enSaBmyd0awpY87lVQnZlyuKTqp82TejIQOlXD0I2TiiFC+Mz/9irwpsllMKxLnN2iLhRQo7cmcD/yyRrMF0WU+byg/vzZOFft0hcuWX6j1VE5zUI32GKVrcu0dhU/v9RdhLOnee/s1uG9N1yBKZw6cQAcBOpz1/XlKjdk32n7iV+9DgqAnFZgSCCYuTCTGFrh3iUpukodvb0BwBgXTr/fNN3V/zUQe+KYc/LPMf3+mVfv7zE6zei3BvTaRx7R1Re+WUSE4+oHsmIB3o2eSXSLyWxflnQ0iujWCU8L6PIoyurYp5JTrwiqi5y4nPSodlxtbCHq9v6CZ+eSv9IeNWLTnjisxzowGJJM73aSepFBakO9sRpnXAV8tjL1NeIyyVTojfVW64uvKsbi3lI0ZRVQp/1OsQXio40zMnulISOOa9fVPEJvVYJ1W638bxA/aPyU5CQ+n8voqCI1IHq+URZREIlXFRDpgUdt8TDvGglij1mFWylvt2fE2ZxvUY0qxLqPVn/DY56g6uY+xWpt3s5nxM+Ej2o1MN8krakYqQa5pzmo+roqxOGXE9I1An19NJEhcg4m81m6h2bqtlWx2GVcKmjxzTMpzBfKSop9daUzKptUCcUUrL+ZIE6oR74VZvpkPGiyPMiX72Tzr+/JAz1Jy6oXjPIhzImrG5sPT3YXTfDOqFcvxPdX/ZS1WWOrPdSHWytuhDx5710rP5KpV8GPMwxcJ9Zn9XnXI/R1wnVTjijcHvqNKLqNGNvp5qLH+ieWXcaeUqYUPVJErsmi8Bv4DUU+kRwL8KqUQTqp1eht1UQ+t5CjPVxuJT12WJShCR9/eEf+myxCaOJV4rNSob1yE0urlwBDVjVaS6DT/9+477RQHtkf+Knxa1LAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAADtD5MzNEQKciDpAAAAAElFTkSuQmCC"
              alt="Wikipedia"
            />
          </div>
          <div @click="goToPage('githubUserSearch')" class="flex-center">
            <img
              class="small-img lg:h-28 img-clickable"
              src="https://encrypted-tbn0.gstatic.com/images?q=tbn:ANd9GcRWzMChN7JnSUz2lr2Eb_pE8Sco8-4aKcngnA&s"
              alt="Git Search"
            />
          </div>
        </div>
        <div @click="goToPage('calculatorComp')" class="lg:row-span-2 flex-center">
          <img
            class="small-img lg:h-auto img-clickable"
            src="data:image/png;base64,iVBORw0KGgoAAAANSUhEUgAAAOEAAADhCAMAAAAJbSJIAAAAb1BMVEUAAAD////7+/vg4ODr6+vExMQ5OTmfn58hISHj4+Ovr6/Z2dkmJiabm5tSUlKNjY309PRiYmJbW1uUlJRCQkKnp6fPz88MDAy3t7f29vZnZ2dMTEx8fHyEhISzs7PMzMwWFhYuLi5zc3NOTk4/Pz+ndKKuAAADgklEQVR4nO2da3OqMBBACYhUbcVXK1oftfX//8ZbvSrZiBZHkTWeM51+WcN4DIRkE0IQAAAAAAAAAAAAAAAAAAAAAAAAAAAAAICf9LPWJLwhk1Y2rdvJphuZCmgN6vY6kFbht2FYt9mOeVWCWhQ/qxM0plu33YZOlYZR3XZBxVWoohKTag3bdfsFwUe1hp26/Sq+DI1p1O0XBJXc7DHEEMNrDK8fVmg3XF97vFfths1rj/eC4d3B8FIwvD8YXgqG9wfDS8Hw/mB4KeoNX68+oHbDZXwlS+2GtwZDDDHEEEMMMdRqOMlmg2laNO0Wz/v9eVwQ6Ayng9li8hCGoVnsIt2WE/pY/Q+8Oj0z09ivnHl/BEOT5jFZjVkeaMsKzAOzBzAUE++9Yg85Nz75sgLusgB9hj0RtKtkZAdWVmAuivTk8fQZvsto/n2dJQd5JYYy8Kbd0FlRmLcpbzIwPAQ+ZGCg3dCZP8yblFQG8sVwCxlQP384ktEShpkMrLQbfstofrk5F2jeZjpL16baDWWNjMNTX9Uq9iUC8lap0DAUyTa7YRRtkN2eyNpVv1JBNI1N8V3HVqRhR+z1h26nVaGhdZ6u5d27kyvK5X69z0PAOUdVGoYm2tVJ6pxwprdrhqYNJ7Bf7Tw6Ho8oNNzQaidJ7PptHbMkyY78Nr9LnCRtdyyi2PCGYIghhhhiiCGGag397tM8Qb/U+7GF9+ND/8f4/udp/M+1+Z8v9T/n7f+8hf9zT/7PH/o/B/wE8/hPsBbD+/U0NwZDDDHEEEMMMdRpGP7+RWcebCrK+/6aLOMo3BbWb2jC4cvZEqujpKhZbjOmX+lxt02jYTT+s8zIHlX9VttsHxgfdWYVGrbKFGqKs3FmRdxzWKHhT6lS9jgwtgNr9YbLksWstL58sDbWbjj7u8SW9imHb+2GZXcBPJkRXms3LPss98mMsPpnufsli+W7ujpXble7Ydk9VfMGRWZY3f1e9RmWuh0GYppQTgRE2g2dDPYpFqd+FDdhqtCw1C1fnopWazpyu94aDd1J0gKc2RcT77uy348xtjCd+bl7xig9XlAzee+Og+asIIms09Cc3T6x6NOHf49jeDMwxBDDEvi/F7T/+3n7vye7//vqV3khhirejfAE77fw/x0lT/CemSd4V1Dg//ueAAAAAAAAAAAAAAAAAAAAAAAAAAAAAOA2/AMzKUJt3Gqb5gAAAABJRU5ErkJggg=="
            alt="Calculator"
          />
        </div>
      </div>
    </div>
  </div>
</template>
