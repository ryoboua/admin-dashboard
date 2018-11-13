<template>
    <div>
      <nav>
        <div class="nav-wrapper indigo">
        <form>
            <div class="input-field">
            <input id="search" type="search" required>
            <label class="label-icon" for="search"><i class="material-icons">search</i></label>
            <i class="material-icons">close</i>
            </div>
        </form>
        </div>
  </nav>
    <div class="nav-section-container grey lighten-3">
      <div class="nav-wrapper black-text">
        <div class="left-align black-text">
          <a href="#!" class="breadcrumb black-text">
            <i class="small material-icons home-icon">home</i>
            <span class="hide-on-small-only">Home</span>
          </a>
          <a href="#!" class="breadcrumb black-text hide-on-small-only"><strong>Dashboard</strong></a>
        </div>
      </div>
        <div class="black-text admin-total-wrapper">
            <p class="mr"> <i class="material-icons">notifications</i><span class="new badge red white-text">{{notification}}</span></p>
            <p class="mr"> <i class="material-icons">message</i><span class="new badge red white-text">{{messages}}</span></p>
            <p class="mr"> <i class="material-icons">settings</i></p>

            <br />
        </div>
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
        margin: 0px 1em 0px auto;
        width: auto;
        flex-wrap: wrap;
        justify-content: flex-end;
    }
    .mr {
        margin-right: 1em;
    }
</style>


