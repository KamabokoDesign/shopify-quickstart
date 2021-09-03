# Shopify Quickstart
Developing custom themes with shopify

## Table of Contents

Developing a Theme
1. [Account Setup](#step-1-account-setup)
2. [Local Theme Dev](#step-2-local-theme-development)
3. [Pull Down Dawn](#step-3-pull-down-the-dawn-starter-theme)
4. [Shopify CLI](#step-4-auth-login-into-your-shopify-store)
5. [Send your theme to Shopify](#step-5-serve-your-theme)

Adding 3D Support
1. [media.liquid]()


## Step 1: Account Setup 
1. Join the [Shopify Partner Program](https://www.shopify.com/partners)
2. Log in to your Partner Dashboard.
3. Click Stores.
4. Click Add store.
5. In the Store type section, select Development store.
6. In the Login information section, enter a name for your store and a password that you can use to log in. By default, the email associated with your Partner Dashboard is used as the username, but you can change it if you want to.
7. Optional: Enable a developer preview by checking Create a non-transferrable store that uses a developer preview. Select a developer preview version from the drop-down list.
8. In the Store address section, enter your address.
9. Optional: In the Store purpose section, select the reason why you're creating this development store.
Click Save.

## Step 2: "Local" Theme Development
Install the Shopify CLI

macOS via Homebrew
```
brew tap shopify/shopify
brew install shopify-cli
```

windows via Ruby
1. Make sure Ruby is installed
```
gem --version
```
2. If you don't have it installed, [download here](https://rubyinstaller.org/downloads/) and restart your computer to make the gem command available on terminal.
3. Then to download Shopify
```
gem install shopify-cli
```

## Step 3: Pull down the Dawn Starter Theme
1. navigate to the working directory where you want to clone Dawn.
2. Enter the following command:
```
shopify theme init
```
3. Name your theme
4. Everything will get pulled down
5. Make sure to cd into your new directory
```
code .
```

## Step 4: Auth login into your Shopify store
Login with the command
```
shopify login --store johns-apparel.myshopify.com
```
Or if you're getting the login error do
```
shopify login --store=johns-apparel.myshopify.com
```

Where johns-apparel.myshopify.com is your development store URL.

After you login make sure to keep the http://127.0.0.1/ window open in your chrome browser. 

## Step 5: Serve your theme
```
shopify theme serve
```

If you run into a bug like below:
```
✗ You are not authorized to edit themes on DOMAIN.
Make sure you are a user of that store, and allowed to edit themes.
```
Follow the [Errors & Fixes](#errors) for a solution.

## Step 6: View your local
After you run the serve, an environment should show up on your local. It could be at http://127.0.0.1:9292. The ports may change depending on your configuration. 

Now when you do changes do your theme, and hit save. Changes will hot-reload into the localhost port.

## Developing your theme

Here's some theme commands for getting started
https://shopify.dev/themes/tools/cli/theme-commands

## Want to customize the checkout process?
Use cases are for products that are federally or locally regulated. i.e. fertilizer may have to have a warning near the item during checkout. 

Here's a [YouTube tutorial](https://www.youtube.com/watch?v=zsyKQ9lT8tQ) to follow along with

And the [official docs](https://shopify.dev/apps/checkout#ui-extensions) on Checkout UI Extensions & Beta Scripts

[Step by Step tutorial](https://shopify.dev/apps/checkout/post-purchase/getting-started-post-purchase-extension) 

## Want to add 3d support?

[Media.liquid](https://shopify.dev/themes/product-merchandising/media/support-media)

## GraphQL Requests
```
	curl -X POST \
	"https://<SHOP>.myshopify.com/admin/api/2019-10/graphql.json" \
	-H "Content-Type: application/graphql" \
	-H "X-Shopify-Access-Token: <ACCESS_TOKEN>" \
	-d '
	{
		shop {
			products(first: 5) {
				edges {
					node {
						id
						handle
					}
				}
			}
		}
	}
```

## Errors
```
✗ You are not authorized to edit themes on DOMAIN.
Make sure you are a user of that store, and allowed to edit themes.
```
Had to create a new account, add it to the store, give it staff permissions. And sign in via that account.

If that doesn't work. Follow the [Caution section here.](https://shopify.dev/themes/tools/cli/getting-started)

```
You can't use Shopify CLI with development stores if you only have Partner staff member access. If you want to use Shopify CLI to work on a development store, then you should be the store owner or create a staff account on the store.

If you're the store owner, then you need to log in to the store directly using the store URL at least once (for example, using my-example-store.myshopify.com/admin) before you log in using Shopify CLI. Logging in to the Shopify admin directly connects the development store with your Shopify login.
```

```
You cannot use gems with Shopify CLI
```
Had to run the command `gem install wdm`
[Source](https://stackoverflow.com/questions/68376154/error-you-cannot-use-gems-with-shopify-cli)



## Resources

[2021 Youtube Follow Along](https://www.youtube.com/watch?v=3aMvc2z5CcY&ab_channel=DavidMartin-UXHACKS)
