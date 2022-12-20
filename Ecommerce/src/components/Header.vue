<script>
	export default{
		data() {
			return {
				cartItems: [{id:0,
							img: 'image-product-1-thumbnail.jpg',
							desc: 'Fall Limited Edition Sneakers',
							price: 125,
							count: 1,
							}],
				menuMobile: false,
				displayCart: false
			}
		},
		methods: {
			removeItem(idx){
				this.cartItems = this.cartItems.filter((o,i) => i != idx)
			},
			toggleMenuMobile(e){
				if(window.innerWidth < 770){
					if(e.target.localName == "ul" || e.target.localName == "a" || e.target.localName == "li")
						e.preventDefault();
					else
						this.menuMobile = !this.menuMobile;
				}
			}
		},
		watch: {
			menuMobile(menuMobile){
				document.querySelector(".box-nav ul").style.display = menuMobile ? 'flex' : 'none';
				document.querySelector(".back-menu-mobile").style.display = menuMobile ? 'block' : 'none';
			},
			displayCart(newDisplay){
				document.querySelector(".box-cart").style.display = newDisplay ? 'block' : 'none';
			}
		}
	}
</script>

<template>
	<header>
		<div class="container">

			<div class="box-nav">
				<div class="logo"></div>
				<nav @click="(e) => toggleMenuMobile(e)">
					<ul>
						<span></span>
						<li><a href="#">Collections</a></li>
						<li><a href="#">Men</a></li>
						<li><a href="#">Women</a></li>
						<li><a href="#">About</a></li>
						<li><a href="#">Contact</a></li>
					</ul>
				</nav>
			</div>

			<div @click="() => displayCart = !displayCart " class="cart">
				<div v-show="cartItems.length > 0" class="count-items-cart">
					<span v-if="cartItems.length <= 99">{{cartItems.length}}</span>
					<span v-else>+99</span>	
				</div>
			</div>

			<div class="img-profile"></div>

			<div class="box-cart">
				<h3>Cart</h3>
				<nav v-if="cartItems.length > 0">

					<div  v-for="(item,index) in cartItems" :key="item.id" class="product-in-cart">
						<img :src="'./src/assets/'+item.img"/>
						<div class="desc-cart-product">
							<p>{{item.desc}}</p>
							<p>{{"$"+item.price+",00"}} x {{item.count}} <b>${{item.price * item.count}},00</b></p>
						</div>
						<button @click="removeItem(index)"></button>
					</div>

					<button>Checkout</button>
				</nav>
				<h3 v-else>Your cart is empty</h3>
			</div>
		</div><!-- CONTAINER -->
		<div class="back-menu-mobile"></div>
	</header>
</template>

<style scoped>
	header{
		padding: 30px 1%;
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
		border-bottom: 2px solid transparent;
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
		width: 5%;
		min-width: 40px;
		padding-top: 5%;
		min-height: 40px;
		background-image: url("../assets/image-avatar.png");
		background-size: 100% 100%;
		background-position: center;
		margin-left: 8px;
		border-radius: 50%;
		cursor: pointer;
		transform: translateY(-50%);

	}
	.box-cart{
		width: 100%;
		max-width: 350px;
		max-height: 300px;
		background-color: #ffffff;
		position: absolute;
		top: 80%;
		right: 0;
		border-radius: 12px;
		box-shadow: 0 12px 25px hsl(0, 0%, 0%, 15%);
		overflow-y: auto;
		z-index: 1;
		display: none;
	}
	.box-cart h3:nth-of-type(1){
		border-bottom: 1px solid hsl(24, 14%, 75%);
		padding: 5%;
	}
	.box-cart h3:nth-of-type(2){
		width: 100%;
		text-align: center;
		padding: 80px 0;
		color: hsl(219, 9%, 45%);
		font-weight: 400;
		font-size: 16px;
	}
	.box-cart nav{
		padding: 2%;
	}
	.box-cart nav > button{
		width: 100%;
		padding: 14px;
		border-radius: 12px;
		border: none;
		color: #ffffff;
		font-weight: 700;
		background-color: hsl(26, 100%, 55%);
		cursor: pointer;
	}
	.product-in-cart{
		display: flex;
		width: 100%;
		flex-wrap: wrap;
		align-items: center;
		margin-bottom: 8px;
		justify-content: left;
		cursor: pointer;
	}
	.product-in-cart img{
		width: 56px;
		height: 56px;
		border-radius: 8px;
	}
	.desc-cart-product{
		max-width: 250px;
		margin-left: 12px;
		color: hsl(219, 9%, 45%);
		font-size: 14px;
	}
	.desc-cart-product b{
		color: hsl(220, 13%, 13%);
	}
	.product-in-cart > button{
		width: 24px;
		height: 24px;
		margin-left: auto;
		border: none;
		background-image: url("../assets/icon-delete.svg");
		background-position: center;
		background-repeat: no-repeat;
		cursor: pointer;
		background-color: transparent;
		border-radius: 4px;
	}
	.product-in-cart > button:hover{
		background-color: hsl(223, 64%, 98%);
	}

	@media screen and (max-width: 770px){
		header{
			padding: 0;
		}
		.container{
			padding: 20px 2%;
		}
		.box-nav{
			min-width: 180px;
			flex-direction: row-reverse;
			align-items: center;
			justify-content: space-around;
		}
		.box-nav nav{
			width: 24px;
			height: 24px;
			background-image: url("../assets/icon-menu.svg");
			background-position: center;
			background-repeat: no-repeat;
			cursor: pointer;
		}
		.box-nav ul{
			position: absolute;
			top: 0;
			left: 0;
			display: flex;
			flex-direction: column;
			flex-wrap: wrap;
			margin-left: 0;
			background-color: #ffffff;
			width: 35vw;
			min-width: 250px;
			height: 100vh;
			padding-top: 50px;
			z-index: 3;
			display: none;
		}
		.box-nav ul > span{
			width: 24px;
			height: 24px;
			position: relative;
			top: -32px;
			left: 5%;
			background-image: url("../assets/icon-close.svg");
			background-position: center;
			background-repeat: no-repeat;
			cursor: pointer;
			z-index: 4;
		}
		.back-menu-mobile{
			z-index: 2;
			width: 100%;
			height: 100vh;
			background-color: hsl(0,0%,0%,75%);
			position: absolute;
			top: 0;
			left: 0;
			display: none;
		}
		.box-nav li{
			padding: 16px 5%;
			display: flex;
			align-items: center;
		}
		.box-nav li:hover{
			border-bottom: 2px solid hsl(26, 100%, 55%);
		}
		.box-nav a{
			color: hsl(220, 13%, 13%);
		}
		.box-cart{
			top: 100px;
		}
		.img-profile{
			transform: translateY(0);
		}
	}
</style>