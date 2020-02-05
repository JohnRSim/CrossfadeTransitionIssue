<script>
	import Nav from "../components/Nav.svelte";

	export let segment;
</script>

<style>
	/* Globals */
	@import '../themes/global.css';
	/*@import '../themes/light.css';
	@import '../themes/dark.css';*/

	#FB-appWrapper {
		position: fixed;
		top: 100px;
		bottom: 0px;
		left: 0px;
		right: 0px;
		max-width: 56em;
		margin: 0 auto;
		box-sizing: border-box;
		display: flex;
		flex-direction: column;
	}

	#FB-appWrapper > main {
		flex:1;
		position: relative;
	}

	#sideSlideDrawer {
		width:18px;
		margin-left:-5px;
		position: fixed;
		top:0px;
		left:0px;
		bottom:0px;
		z-index:10;
	}
	#swipableDrawer {
		position: fixed;
		top:0px;
		left:0px;
		bottom:0px;
		right:0px;
		z-index:25;
		overflow:hidden;
		background: rgba(0,0,0,0.23);
		transition: background 0.3s;
		/*border:solid 1px red;*/
	}
	#swipableDrawer.mousedown,
	#drawerMenu.mousedown {
		transition:none;
	}

	#drawerMenu {
		display: flex;
		flex-direction: column;
		position: fixed;
		top: var(--statusbar-height, 0px);
		left:0px;
		bottom:0px;
		z-index:30;
		background:#fff;
		width:300px;
		transform: translateX(0%);
		transition: 0.5s ease-out;
	}
	#profilePanel {
		background-image: url("/bg_profileShapes.svg");
		background-position:right;
		background-size: cover;
		background-repeat:no-repeat;
		min-height:100px;
		padding:10px 20px;
		/*box-shadow:inset 0px -1px 0px 0px #F1F1F1; */
		border-bottom: 0.1px solid #F1F1F1;
		background-color: rgba(0,0,0,0) !important;
	}
	#profileAvatar {
		border-radius:400px;
		width:90px;
		margin-bottom:8px;
	}

	.sep {
		/*box-shadow:inset 0px -1px 0px 0px #F1F1F1; */
		border-bottom: 0.1px solid #F1F1F1;
		background-color: rgba(0,0,0,0) !important;
	}

	#sideDrawerNav {
		overflow:scroll;
		flex:1;
	}
	#sideDrawerFooter ul,
	#sideDrawerNav ul {
		margin:0px;
		padding:0px;
	}
	#sideDrawerFooter li,
	#sideDrawerNav li {
		list-style:none;
		padding:10px 20px;
	}
	#sideDrawerFooter {
		background:#0F1626;
		color: #fff;
	}

	#appVersion {
		background:#1F2D4E;
		color:#7485AD;
		text-align: right;
		padding:5px 10px;
	}
	h1, h2 {
		margin:0px;
		font-size:1em;
	}
	h2 {
		font-size:0.9em;
		opacity:0.8;
	}

</style>

<Nav {segment}/>

<!-- App Body Footer -->
<div id="FB-appWrapper">
	<main>
		<slot></slot>
	</main>
</div>
<!-- xApp Body Footer -->