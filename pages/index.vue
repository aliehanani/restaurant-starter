<template>
	<div class="home-page">
		<hero-section>
			<h1
				class="text-4xl md:text-5xl font-black pt-0 pb-1 mb-0 lh-none break-word"
				:class="{'uppercase tracking-wide': themeInfo.theme === 'modern'}"
			>{{siteInfo.name}}</h1>
			<divider />
			<p
				class="w-full max-w-md mx-auto text-xl md:text-2xl font-bold py-4 mb-4 lh-none font-feature"
			>{{siteInfo.description}}</p>
			<div class="mb-6">
				<nuxt-link
					to="/menu"
					class="bg-brand text-brand_contrast text-lg font-bold uppercase tracking-wider shadow p-3"
				>View our Menu</nuxt-link>
			</div>
		</hero-section>
		<!-- <div class="w-full container mx-auto pt-16 pb-8 px-4">
			<div
				class="bg-gray-100 w-full flex items-center justify-center py-6"
				style="padding-bottom: -75px;"
			>
				<script
					type="text/javascript"
					src="//www.opentable.com/widget/reservation/loader?rid=1041577&type=standard&theme=wide&iframe=true&overlay=false&domain=com&lang=en-US"
				></script>
			</div>
		</div>-->
		<div class="w-full container mx-auto flex flex-wrap items-stretch py-8">
			<div class="w-full md:w-1/2 lg:w-1/3">
				<location-card class="h-full m-4" />
			</div>
			<div class="w-full md:w-1/2 lg:w-1/3 md:my-0 my-8">
				<hours-card class="h-full m-4" />
			</div>
			<div class="w-full md:w-1/2 lg:w-1/3">
				<location-card class="h-full m-4" />
			</div>
		</div>
		<div class="w-full container mx-auto px-4 py-8">
			<div
				class="flex lg:flex-row-reverse flex-wrap items-stretch"
				:class="{'bg-gray-900': themeInfo.is_dark, 'bg-gray-100': !themeInfo.is_dark}"
			>
				<div
					class="w-full lg:w-1/2 bg-cover"
					:style="`min-height: 400px; background-image: url(/images/uploads/bg.jpg);`"
				></div>
				<div class="w-full lg:w-1/2 px-4 sm:px-6 md:px-8 py-10 xl:py-16">
					<div class="w-full max-w-lg mx-auto">
						<h2 class="text-3xl lg:text-4xl font-black">About Us</h2>
						<p
							class="text-lg py-4"
						>If you are looking for a place in Kuala Lumpur where you can kick back and have good food and drinks, drop by Afghan Kitchen. Located in the heart of the bustling neighborhood of Ampang, our restaurant boasts a Traditional Afganistan menu that is rooted in Afghan cooking techniques. We offer a range of dishes that everyone can enjoy, including rice, appetizers, and warm tea.</p>
						<nuxt-link
							to="/about"
							class="inline-flex items-center"
							:aria-label="`Learn more about ${siteInfo.name}`"
							:title="`Learn more about ${siteInfo.name}`"
						>
							<span
								class="font-bold uppercase tracking-wider text-sm py-1 mr-3 border-b-2 border-brand"
							>Learn more</span>
							<svg
								viewBox="0 0 24 24"
								width="20"
								height="20"
								stroke="currentColor"
								stroke-width="2"
								fill="none"
								stroke-linecap="round"
								stroke-linejoin="round"
							>
								<polyline points="9 18 15 12 9 6" />
							</svg>
						</nuxt-link>
					</div>
				</div>
			</div>
			<ul class="pt-4 auto-sized-grid">
				<li v-for="i in 8" :key="i">
					<img
						:src="`https://source.unsplash.com/random//600x400/?afghanistan-landscape=${i}`"
						:alt="`Image ${i} from Unsplash.com`"
						loading="lazy"
					/>
				</li>
			</ul>
		</div>
	</div>
</template>

<script>
import * as themeInfo from "~/assets/content/config/theme.json";
import HeroSection from "~/components/HeroSection";
import HoursCard from "~/components/HoursCard";
import LocationCard from "~/components/LocationCard";
import Divider from "~/components/Divider";

export default {
	layout: themeInfo.theme,
	computed: {
		siteInfo() {
			return this.$store.state.siteInfo;
		},
		contactInfo() {
			return this.$store.state.contact.info;
		},
		socialInfo() {
			return this.$store.state.social.info;
		},
		themeInfo() {
			return this.$store.state.theme.info;
		},
		menuInfo() {
			return this.$store.state.menu.fullMenu;
		}
	},
	components: {
		HeroSection,
		HoursCard,
		LocationCard,
		Divider
	}
};
</script>

<style>
/* .hours-operation dt {
	float: left;
}
.hours-operation dd {
	float: right;
}
.hours-operation dd:after {
	content: "\A";
	white-space: pre;
} */
.auto-sized-grid {
	display: grid;
	grid-gap: 1rem;
	grid-template-columns: repeat(auto-fit, minmax(150px, 1fr));
}
@media screen and (min-width: 768px) {
	.auto-sized-grid {
		grid-template-columns: repeat(auto-fit, minmax(300px, 1fr));
	}
}
</style>
