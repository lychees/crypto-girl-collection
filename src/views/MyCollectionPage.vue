<template>
<div>

	<section>
		<div class="userContainer">
			<div class="usericon">
				<img class="iconimg" alt="" width="100" srcset="../assets/usericon.jpg"/>
			</div>
			<div class="usercontent">
				<p class="useraddress">useraddress0xaaaaaaaaaaaaa</p>
			</div>
		</div>
    </section>

	<section>
      <div class="columns is-multiline is-mobile section2div">
        <div class="column is-4-desktop is-4-tablet is-12-mobile cardItem" v-for="item in itemIds" :key="item.id"
        @click="gotoCoinProfile(item.code)">
        	<img class="cardItemImg" alt="" :src="item.img"/>
        	<div :style="{ backgroundColor: item.color, height: '50px' }">
        		<span>
			        <a :style="{ lineHeight: '50px', color: item.textcolor, paddingLeft: '20px' }">{{ item.name }}{{ item.code }}</a>
			    </span>
			    <span class="priceSpan">
			        <a :style="{ lineHeight: '50px', color: item.textcolor }">{{ item.name }}USD</a>
			    </span>
        	</div>
        </div>
      </div>
    </section>

</div>
</template>

<script>
export default {
  name: 'MyCollectionPage',
  data: () => ({
    itemIds: []
  }),
  methods: {
    gotoCoinProfile(code) {
      this.$router.push({ path: `/coin/${code}` })
    }
  },
  mounted() {
    this.$http.get('static/girl_cards.json').then((response) => {
      this.itemIds = response.body;
    });
  }
};
</script>

<style scoped>
/*
  section 1
*/
.userContainer {
	background-image: url("../assets/collection_bk.png");
	background-size: 100%;
	background-repeat: no-repeat;
	background-color: #fff;
	width: 100%;
	/*padding-top: 43.5%;*/
	padding-top: 28%;
	position: relative;
	text-align: center;
}
.usericon {
  position: absolute;
  top: 0;
  left: 0;
	width: 100%;
	padding-top: 60px;
}
.iconimg{
	border-radius: 50%;
    display: block;
    margin-left: auto;
    margin-right: auto;
}
.usercontent {
	position: absolute;
  top: 0;
  left: 0;
  width: 100%;
  text-align: center;
	padding-top: 15%;
}
.useraddress {
	color: #08567e;
}

/*
  section 2
*/
.section2div {
	padding-right: 50px;
	padding-left: 50px;
	padding-top: 30px;
	padding-bottom: 50px;
}
.cardItemImg{
	vertical-align:bottom;
	cursor: pointer;
}
.priceSpan {
	float:right;
	padding-right: 20px;
}

@media (max-width: 800px) {
	.cardContainer {
		background-size: cover;
		padding-top: 60%;
	}
	.charaimg{
		width: 100%;
	}
	.btnContainer {
		padding-top: 50%;
	}

	.section2div {
		padding-top: 100px;
	}
	.cardItemImg{
		width: 100%;
	}
}
</style>

