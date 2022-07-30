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

<br/>

## Developing your theme

Here's some theme commands for getting started
https://shopify.dev/themes/tools/cli/theme-commands

If you want to overwrite a theme on current store 
```
shopify theme push
```
If you want to republish i.e. publish changes to a theme's name do
```
shopify theme publish
```

</br>

## Changing the name of your theme, you'll find it in

config > settings_schema.json
```
"theme_name"
"theme_version"
"theme_author"
```

## Adding the Color Themes

You can create different color themes @ this file:
```
settings_data.json
```

To add another one you can add it in the `presets`: 

```
"Craft": {
  "colors_solid_button_labels": "#EFECEC",
  "colors_accent_1": "#2A332F",
  "colors_accent_2": "#476154",
  "colors_text": "#1C1A1A",
  "colors_outline_button_labels": "#7B8382",
  "colors_background_1": "#EFECEC",
  "colors_background_2": "#C1BCAE",
  "type_header_font": "americana_n4",
  "type_body_font": "quattrocento_sans_n4",
  "sections": {
     "footer": {
      "type": "footer",
      "settings": {
        "color_scheme": "accent-1"
       },
      "blocks": {
        "menu": {
        "type": "link_list"
         },
         "text": {
           "type": "text"
          }
       },
       "block_order": [
         "menu",
         "text"
       ]
   }
   }
}
```

[This is how you change the color in the Shopify Admin](https://help.shopify.com/en/manual/online-store/themes/os/theme-structure/theme-settings?shpxid=e7ae3a7a-5D89-4F1C-6ACD-0A0105E78D90#change-theme-styles)

[Source](https://www.webibazaar.com/blog/tutotial/how-to-change-theme-colors-of-your-online-store-shopify-themes/)

## Changing the Font
[Source](https://shopify.dev/themes/architecture/settings/fonts#available-fonts)


## Where to put svgs?

In the snippets folder! You'll name your file like `icon-brandlogo.liquid` and just drop in the <svg> data there.


## Assets Folder 
[Why you can't create subdirectories as of 2.0](https://community.shopify.com/c/technical-q-a/a-folder-in-assets-breaks-shopify-theme-serve/m-p/1328291)

## Templates 
[Official Docs](https://shopify.dev/themes/store/requirements)

404
```
1. sections > main-404.liquid     //template for 404 pages
2. css > section-main-404.css     //accompanying css
```

Article
```
1. sections > main-article.liquid
2. css > section-blog-post.css
3. templates > article.json		  //REQUIRED THEME FILE
```

Blog
```
1. sections > main-blog.liquid
2. css > component-article-card.css, component-card.css, section-main-blog.css
3. templates > blog.json
```

Cart
```
1. sections > cart-items, cart-footer, featured-products
2. css >
3. templates > cart.json
```

Collection
```
1. sections > banner, product-grid
2. css >
3. templates >
```

Gift_Card
```
1. sections > 
2. css >
3. templates >
```

List-Collections
```
1. sections > 
2. css >
3. templates >
```

Page.Contact
```
1. sections > 
2. css >
3. templates >
```

Page
```
1. main-page.liquid               //template used for non-shop pages (contact, faq, etc.)
2. section-main-page.css          //accompanying css
3. templates > page.json          //REQUIRED 
```

Password
```
1. sections > 
2. css >
3. templates >
```

Product
```
1. sections > 
2. css >
3. templates >
```

Search
```
1. sections > 
2. css >
3. templates >
```


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
1. Had to create a new account, add it to the store, give it staff permissions. And sign in via that account.
2. If that doesn't work. Follow the [Caution section here.](https://shopify.dev/themes/tools/cli/getting-started)



Basically just do a 
```
shopify logout
```
and logout from the store on the Shopify Admin. 

Then re-log into the /admin in the Shopify web view. 

Do the shopify login in your terminal one more time, it should work.


```
You can't use Shopify CLI with development stores if you only have Partner staff member access. If you want to use Shopify CLI to work on a development store, then you should be the store owner or create a staff account on the store.

If you're the store owner, then you need to log in to the store directly using the store URL at least once (for example, using my-example-store.myshopify.com/admin) before you log in using Shopify CLI. Logging in to the Shopify admin directly connects the development store with your Shopify login.
```

```
You cannot use gems with Shopify CLI
```
Had to run the command `gem install wdm`
[Source](https://stackoverflow.com/questions/68376154/error-you-cannot-use-gems-with-shopify-cli)

## Should I Use GraphQL or REST?
GraphQL is faster :) it only fetches what it needs. If you only want product.id and product.image, it'll just give you those 2 properties. On the other hand, rest will give you the whole product object, with data like product.id, product.image, product.metafields, and product.variants.

[Playground 2 Test GraphQL Requests](https://shopify.dev/apps/tools/graphiql-admin-api)
[A good video overview](https://www.youtube.com/watch?v=yY2h4VNlGB0&t=299s)

	
👆 Generally I use GraphQL to create features like "Favorites" / "Wishlists" / "Saved Products". Here's an example GraphQL request.
```
mutation {
  customerUpdate(input: {id: "gid://shopify/Customer/958361468984", tags: ["Test tag, New tag"]}) {
    customer {
      id
      tags
    }
  }
```
[Here's the source for this capability](https://shopify.dev/api/examples/customer-data)



## Resources

[2021 Youtube Follow Along](https://www.youtube.com/watch?v=3aMvc2z5CcY&ab_channel=DavidMartin-UXHACKS)
