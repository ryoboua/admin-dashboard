<template>
    <div class="nav-section-container" >
      <div class="nav-wrapper black-text">
        <div class="left-align black-text">
          <a href="#!" class="breadcrumb black-text">
            <i class="small material-icons home-icon">home</i>
            Home
          </a>
          <a href="#!" class="breadcrumb black-text">Dashboard</a>
        </div>
      </div>
      <div class="black-text admin-total-wrapper">
            <p class="mr"> ${{ totalIncome }} Total Income</p>
            <p class="mr"> {{ newUsers }} New Users</p>
        </div>
    </div>
</template>

<script>
export default {
    name: 'NavSection',
    props: {
        name: {
            type: String,
            default: 'Default Name'
        },
        imgURL: {
            type: String,
            default: 'Default Name'
        },
        totalIncome: {
                type: Number,
                default: 34,
        },
        newUsers: {
            type: Number,
            default: 20
        },
        notification: {
            type: Number,
            default: 0
        },
        messages: {
            type: Number,
            default: 4
        }
    },
}
</script>

<style scoped>
    .breadcrumb:before {
    color: black;
    }
    .nav-section-container {
        background-color: white;
        height: 56px;
        line-height: 56px;
        display: flex;
        width: 100%;
    }

    .home-icon {
        margin: 15px 1em 0em;
    }

    .admin-total-wrapper {
        line-height: 0px;
        display: flex;
        margin: 13px 1em 0px auto
    }

    .mr {
        margin-right: 1em;
    }
</style>


