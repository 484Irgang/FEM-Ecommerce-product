<script>
	export default{
		data() {
			return {
				count: 0
			}
		}
	}
</script>

<template>
	<header>
		<div class="container">

			<div class="box-nav">
				<div class="logo"></div>
				<ul>
					<li><a href="#">Collections</a></li>
					<li><a href="#">Men</a></li>
					<li><a href="#">Women</a></li>
					<li><a href="#">About</a></li>
					<li><a href="#">Contact</a></li>
				</ul>
			</div>

			<div class="cart">
				<div v-show="count > 0" class="count-items-cart">
					<span v-if="count <= 99">{{count}}</span>
					<span v-else>+99</span>	
				</div>
			</div>
			<div class="img-profile"></div>

			<div class="box-cart">
				<h3>Cart</h3>
				<nav>
					<div class="product-in-cart">
						<div class="img-cart-product"></div>
						<div class="desc-cart-product">
							<p>Fall Limited Edition Sneakers Ffiofjdiosfjiosdflsdkfjsdifjsdiofsd</p>
							<p>$125,00 x 3 <b>$375,000</b></p>
						</div>
					</div>
					<button>Checkout</button>
				</nav>
			</div>
		</div><!-- CONTAINER -->
	</header>
</template>

<style scoped>
	header{
		padding: 30px 6% 0 2%;
	}
	.container{
		position: relative;
		display: flex;
		flex-wrap: wrap;
		align-items: center;
		justify-content: space-between;
		border-bottom: 1px solid hsl(220, 14%, 75%);
	}
	.box-nav{
		display: flex;
	}
	.logo{
		width: 150px;
		height: 50px;
		background-image: url("../assets/logo.svg");
		background-position: center;
		background-repeat: no-repeat;
	}
	.box-nav ul{
		display: flex;
		flex-wrap: wrap;
		margin-left: 25px;
	}
	.box-nav li{
		padding: 18px 15px 60px 15px;
		display: flex;
		align-items: center;
	}
	.box-nav li:hover{
		border-bottom: 2px solid hsl(26, 100%, 55%);
	}
	.box-nav a{
		text-decoration: none;
		color: hsl(219, 9%, 45%);
		font-weight: 400;
	}
	.box-nav li:hover a{
		color: hsl(220, 13%, 13%);
	}
	.cart{
		width: 50px;
		height: 50px;
		background-image: url("../assets/icon-cart.svg");
		background-size: 50% 50%;
		background-position: center;
		background-repeat: no-repeat;
		margin-left: auto;
		align-self: flex-start;
		border-radius: 50%;
		cursor: pointer;
		position: relative;
	}
	.count-items-cart{
		width: 20px;
		height: 20px;
		background-color: hsl(26, 100%, 55%);
		position: absolute;
		right: 0;
		border-radius: 50%;
		display: flex;
		align-items: center;
		justify-content: center;
	}
	.count-items-cart span{
		color: #FFFFFF;
		font-size: 12px;
		font-weight: 700;
	}
	.img-profile{
		width: 60px;
		height: 60px;
		background-image: url("../assets/image-avatar.png");
		background-size: 100% 100%;
		background-position: center;
		margin-left: 20px;
		align-self: flex-start;
		border-radius: 50%;
		cursor: pointer;

	}
	.box-cart{
		width: 100%;
		max-width: 350px;
		max-height: 300px;
		background-color: red;
		position: absolute;
		top: 80%;
		right: 0;
		border-radius: 12px;
		box-shadow: 0 12px 25px rgba(0,0,0,0.5);
		overflow-y: auto;
	}
	.box-cart h3{
		border-bottom: 1px solid hsl(24, 14%, 75%);
		padding: 5%;
	}
	.box-cart nav{
		padding: 5%;
	}
	.box-cart nav button{
		width: 100%;
		padding: 14px;
		border-radius: 12px;
		border: none;
	}
	.product-in-cart{
		display: flex;
		width: 100%;
		flex-wrap: wrap;
		background-color: blue;
		justify-content: space-around;
		align-items: center;
		margin-bottom: 8px;
	}
	.img-cart-product{
		width: 48px;
		height: 48px;
		background-color: green;
		border-radius: 8px;
	}
	.desc-cart-product{
		max-width: 250px;
	}
</style>