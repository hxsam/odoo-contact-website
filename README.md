# Contact Website Odoo Module

[Odoo](https://www.odoo.com) module to open a website in a new tab instead of the current window when using the default contact template. 

## Synopsis

By default links will open in the current window.

You don't want to replace your page when a user clicks the link to open a partner's website.

This module makes it possible to open the website in a new tab!

## Installation

0. Activate the Odoo developer mode (Settings tab)
0. Update Apps List (Apps tab)
0. Remove "Apps" from the search field
0. Search and Install the "Contact Website" module

## Usage

Add `"target_blank": "true"` to `t-options`.

## Example

Assuming you installed the "Contacts Directory" and "Resellers" modules,
via the UI Editor, change the template "website_partner.partner_detail" to:

```xml
<?xml version="1.0"?>
<t name="Partner Details" t-name="website_partner.partner_detail">
    <t t-call="website.publish_management">
        <t t-set="object" t-value="partner"/>
        <t t-set="publish_edit" t-value="True"/>
    </t>
    <h1 class="col-md-12 text-center" id="partner_name" t-field="partner.display_name"/>
    <div class="col-md-4">
        <div t-field="partner.image" t-options="{&quot;widget&quot;: &quot;image&quot;, &quot;class&quot;: &quot;center-block mb16&quot;}"/>
        <address class="well">
             <div t-field="partner.self" t-options="{&quot;widget&quot;: &quot;contact&quot;, &quot;target_blank&quot;: &quot;true&quot;, &quot;fields&quot;: [&quot;address&quot;, &quot;website&quot;, &quot;phone&quot;, &quot;fax&quot;, &quot;email&quot;]}"/>
        </address>
        <t t-raw="left_column or ''"/>
    </div>
    <div class="col-md-8 mt32">
        <t t-if="partner">
            <div t-field="partner.website_description"/>
            <t groups="website.group_website_publisher">
                <h2 class="css_non_editable_mode_hidden">Short Description for List View</h2>
                <div class="css_non_editable_mode_hidden" t-field="partner.website_short_description"/>
            </t>
        </t>
        <t t-raw="right_column or ''"/>
    </div>
</t>
````

Instead of opening the website of your partners in the current window a new tab will be used.
