# Absolute Theme for Magento 2

## Installation
### Setting Up
* Disable Magento `WYSIWYG` editor in `Stores > Configuration > General > Content Management`

### Add homepage content
* Go to `Content > Pages` and press `Add New Page`
* On `Design` tab select `2 columns with right bar` in `Layout` dropdown
* In `Layout Update XML` add following content:
```xml
<referenceContainer name="sidebar.additional">
    <block class="Magento\Cms\Block\Block" name="homepage_callout" before="-">
        <arguments>
            <argument name="block_id" xsi:type="string">homepage_callout</argument>
        </arguments>
    </block>
    <block class="Magento\Newsletter\Block\Subscribe" name="form.subscribe.right" as="subscribe_right" template="subscribe_right.phtml"/>
</referenceContainer>
<referenceContainer name="page.bottom">
    <block class="Magento\Cms\Block\Block" name="featured">
        <arguments>
            <argument name="block_id" xsi:type="string">featured</argument>
        </arguments>
    </block>
</referenceContainer>
```
* On `Content` tab place following code in `Content` field:
```html
<div class="homepage-slider" >
    <div data-mage-init='{"slick": {"slidesToShow": 1, "slidesToScroll": 1, "dots": true, "autoplay": true}}'>
        <div style="margin-right: 10px"><img src="{{view url="images/slider/slide1.jpg"}}" alt=""/></div>
        <div style="margin-right: 10px"><img src="{{view url="images/slider/slide2.jpg"}}" alt=""/></div>
        <div style="margin-right: 10px"><img src="{{view url="images/slider/slide3.jpg"}}" alt=""/></div>
    </div>
</div>
<p>{{widget type="Magento\Catalog\Block\Product\Widget\NewWidget" display_type="new_products" products_count="8" template="product/widget/new/content/new_grid.phtml"}}</p>
```

### Add static blocks
Block **Slogan**

* id: `slogan`
* content: 
```html
<div class="slogan" >
    <img src="{{view url="images/slogan.gif"}}" alt="" />
</div>
```

Block **Footer Contacts**
* id: `footer_contacts`
* content: 
```
Company Name | USA, NY, Street Address | Phone: 1-800-000-0000
```

Block **Footer Additional**
* id: `footer_additional`
* content: 
```html
<div class="footer-additional">
    <div class="footer-contacts" >{{widget type="Magento\Cms\Block\Widget\Block" template="widget/static_block/default.phtml" block_id="footer_contacts"}}</div>
    <div class="footer-payments" >{{widget type="Magento\Cms\Block\Widget\Block" template="widget/static_block/default.phtml" block_id="footer_payments"}}</div>
</div>
```

Block **Footer Links**
* id: `footer_links_block`
* content: 
```html
<div class="box informational">
    <ul>
        <li>
            <h4>About us</h4>
            <ul>
                <li><a href="{{store direct_url="about"}}">About Us</a></li>
                <li><a href="{{store direct_url="our-company"}}">Our company</a></li>
                <li><a href="{{store direct_url="catalog/seo_sitemap/category"}}">Sitemap</a></li>
            </ul>
        </li>
        <li>
            <h4>Customer information</h4>
            <ul>
                <li><a href="{{store direct_url="contacts"}}">Contact Us</a></li>
                <li><a href="{{store direct_url="price-matching"}}">Price matching</a></li>
                <li><a href="{{store direct_url="testimonials"}}">Testimonials</a></li>
            </ul>
        </li>
        <li>
            <h4>Security &amp; privacy</h4>
            <ul>
                <li><a href="{{store direct_url="privacy"}}">Privacy Policy</a></li>
                <li><a href="{{store direct_url="safe-shopping"}}">Safe &amp; secure shopping</a></li>
                <li><a href="{{store direct_url="terms"}}">Terms &amp; conditions</a></li>
            </ul>
        </li>
        <li class="last">
            <h4>Shipping &amp; returns</h4>
            <ul>
                <li><a href="{{store direct_url="delivery"}}">Delivery information</a></li>
                <li><a href="{{store direct_url="guarantees"}}">Satisfaction guarantee</a></li>
                <li><a href="{{store direct_url="returns"}}">Returns policy</a></li>
            </ul>
        </li>
    </ul>
</div>
```
Block **Footer Payments**
* id: `footer_payments`
* content: 
```html
<ul class="footer-payments" >
    <li><img src="{{view url="images/payments/amex.svg"}}" alt=""></li>
    <li><img src="{{view url="images/payments/visa.svg"}}" alt=""></li>
    <li><img src="{{view url="images/payments/maestro.svg"}}" alt=""></li>
    <li><img src="{{view url="images/payments/mastercard.svg"}}" alt=""></li>
</ul>
```
Block **Homepage Callouts**
* id: `homepage_callout`
* content: 
```html
<div class="home-callouts">
    <div class="callout callout1">
        <img src="{{view url="images/callout1.png"}}" alt="" />
    </div>
    <div class="callout callout2">
        <img src="{{view url="images/callout2.png"}}" alt="" />
    </div>
</div> 
```

Block **Featured Products**

##### Create `featured` product attribute: 

- Go to `Stores > Attributes > Product` and press `Add New Attribute`
- Set `Default label` to `Featured` and `Catalog Input Type for Store Owner` to `Yes/No`
- Press `Save Attribute` button
- Go to `Stores > Attributes > Attribute Sets`
- Select your attribute set
- Drag `featured` attribute from `Unassigned Attributes` to `Product Details` group
- Press `Save` button
- Now you can go to `Products > Catalog` and set `Featured` to `Yes` for products you need

##### Create static block

- Go to `Content > Elements > Blocks` and press `Add New Block`
- Set 
 - Block Title : Featured Products
 - Identifier : featured
 - Content : 

```txt
{{widget type="Magento\CatalogWidget\Block\Product\ProductsList" title="Featured Products" products_count="10" template="product/featured.phtml" conditions_encoded="a:1:[i:1;a:4:[s:4:`type`;s:50:`Magento|CatalogWidget|Model|Rule|Condition|Combine`;s:10:`aggregator`;s:3:`all`;s:5:`value`;s:1:`1`;s:9:`new_child`;s:0:``;]]"}}
```

- Press `Save Block` button.
