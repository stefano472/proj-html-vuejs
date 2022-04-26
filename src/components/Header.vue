<template>
  <header>
    <div class="top-header container flex-row font-09">
      <a href="#" class="flex-row">
        <img src="@/assets/dark-pet-logo.png" alt="logo">
      </a>
      <div class="search-bar flex-row">
        <button class="submit">
          <font-awesome-icon icon="fa-solid fa-magnifying-glass" />
        </button>
        <input type="text" class="input font-07" placeholder="Search...">
      </div>
      <div class="question">
        <b>Questions? </b>
        <span>Call us: 1.800.123.4567</span>
      </div>
      <div class="icons flex-row">
        <font-awesome-icon icon="fa-solid fa-bag-shopping" />
        <font-awesome-icon icon="fa-regular fa-user" />
      </div>
    </div>
    <div class="bottom-header">
      <ul class="flex-row container font-09">
        <li v-for="{active, item} in arrayMenuList" :key="item">
          <a href="#" @click="changeActiveStatus()" :class="{active}">{{item}}</a>
        </li>
      </ul>
    </div>
  </header>
</template>

<script>
// import arrayMenuList from "@/data/header.json"

export default {
    name: "HeaderComponent",
    data() {
      return {
        arrayMenuList: [{
            "active": true,
            "item": "Home"
        },
        {
            "active": false,
            "item": "Shop"
        },
        {
            "active": false,
            "item": "About"
        },
        {
            "active": false,
            "item": "Blog"
        },
        {
            "active": false,
            "item": "Contact"
        },
        {
            "active": false,
            "item": "Shop by brand"
        }]
      }
    },
    methods: {
      changeActiveStatus() {
        
        this.arrayMenuList.map((item, index) => {
          if (item[index].active === false) {
            return item[index].active = true

          }
        })
      }
    }
}
//     {
//         "active": true,
//         "item": "Home"
//     },
//     {
//         "active": false,
//         "item": "Shop"
//     },
//     {
//         "active": false,
//         "item": "About"
//     },
//     {
//         "active": false,
//         "item": "Blog"
//     },
//     {
//         "active": false,
//         "item": "Contact"
//     },
//     {
//         "active": false,
//         "item": "Shop by brand"
//     }
</script>

<style lang="scss" scoped>
@use '@/style/variables' as *;

.active {
    color: $text-black !important;
}
header {
  --size: 2rem;
  .top-header{
    justify-content: space-between;
    img {
      height: var(--size);
    }
    .search-bar {
      border-radius: 50px;
      background: $bg-search-bar;
      height: var(--size);
      padding: 0.1rem;
      .submit {
        cursor: pointer;
        border: 0;
        border-radius: 50%;
        background: $btn-bg-secondary;
        width: var(--size);
        height: var(--size);
        color: $bg-search-bar;
        &:hover {
          color: $text-black
        }
      }
      .input {
        width: 15rem;
        padding: 0 1rem;
        border: 0;
        background: transparent;
        &::placeholder {
          color: $text-black;
        }
        &:focus {
          outline: 0;
        }
      }
    }
    .icons {
      gap: 1rem;
      &>* {
        cursor: pointer;
        width: calc(var(--size) / 1.8);
        height: calc(var(--size) / 1.8);
        &:hover {
          color: $text-subtitle;
        }
      }
    }
  }
  .bottom-header {
    box-shadow: 0 -1px 0 $bg-search-bar;
    ul {
      list-style: none;
      justify-content: center;
      gap: 2rem;
      li {
        cursor: pointer;
        a {
          color: $text-secondary;
          text-decoration: none;
          &:hover {
            color: $text-primary;
          }
        }
      }
    }
  }
}
</style>