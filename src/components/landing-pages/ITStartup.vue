<template>
  <div>
    <Banner></Banner>
    <BoxesArea></BoxesArea>
    <ReseauxInformatiques></ReseauxInformatiques>
    <Programmation></Programmation>
    <!-- <Features></Features>
        <Team></Team>
        <Funfacts></Funfacts>
        <Works></Works>
        <Pricing></Pricing>
        <Feedback></Feedback>

         Start Ready To Talk Area 
		<section class="ready-to-talk">
			<div class="container">
				<h3>Ready to talk?</h3>
				<p>Our team is here to answer your question about StartP</p>
				<a href="#" class="btn btn-primary">Contact Us</a>
				<span><a href="#">Or, get started now with a free trial</a></span>
			</div>
		</section>
		End Ready To Talk Area

        <Partner></Partner> 
        <Blog></Blog>-->
  </div>
</template>

<script>
import Banner from "./it-startup/Banner";
import BoxesArea from "./it-startup/BoxesArea";
import ReseauxInformatiques from "./it-startup/ReseauxInformatiques.vue";
import Programmation from "./it-startup/Programmation.vue";
// import Features from './it-startup/Features';
// import Team from './it-startup/Team';
// import Funfacts from './it-startup/Funfacts';
// import Works from './it-startup/Works';
// import Pricing from './it-startup/Pricing';
// import Feedback from './it-startup/Feedback';
// import Partner from './it-startup/Partner';
// import Blog from './it-startup/Blog';
export default {
  name: "ITStartup",
  components: {
    Banner,
    BoxesArea,
    ReseauxInformatiques,
    Programmation,
  },
};
</script>
