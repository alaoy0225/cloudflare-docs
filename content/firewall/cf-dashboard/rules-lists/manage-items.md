---
pcx_content_type: how-to
title: Manage IP List items
weight: 2
---

# Manage IP List items

## View items in an IP List

1. [Access the Lists interface](/firewall/cf-dashboard/rules-lists/) available at **Manage Account** > **Configurations** > **Lists**.

1. Select **Edit** next to the list you want to view.

The list of items displays sorted by IP address, ascending:

![List interface in the Cloudflare dashboard displaying the ordered list items of an IP List](/firewall/static/lists-view-items-in-list.png)

{{<Aside type="note" header="Note">}}

You cannot download a list in CSV format from the dashboard. If you need to download the contents of a list to your device, use the [Get lists](https://api.cloudflare.com/#lists-get-lists) operation to fetch them.

{{</Aside>}}

## Add items to a list

IP Lists support:

- Individual IPv4 addresses
- IPv4 CIDR ranges with a prefix from `/8` to `/32`
- IPv6 CIDR ranges with a prefix from `/4` to `/64`

You can combine individual addresses and CIDR ranges in the same list.

{{<Aside type="note" header="Note">}}

To specify an IPv6 address, enter it as a CIDR range with a `/64` prefix, the largest supported prefix for IPv6 CIDR ranges.

For example, instead of `2001:db8:6a0b:1a01:d423:43b9:13c5:2e8f`, enter one of the following:

- `2001:db8:6a0b:1a01:0000:0000:0000:0000/64`
- `2001:db8:6a0b:1a01::/64` (using the [double colon notation](https://tools.ietf.org/html/rfc5952#section-4.2))

{{</Aside>}}

You can use uppercase or lowercase characters for IPv6 addresses in lists. However, when you save the list, uppercase characters are converted to lowercase.

To add items to an IP List:

1. [Access the Lists interface](/firewall/cf-dashboard/rules-lists/) available at **Manage Account** > **Configurations** > **Lists**.

1. Select **Edit** next to the list you want to edit.

1. Select **Add items**.

1. To [add items to the list manually](#add-items-to-a-list-manually), use the text inputs in the Lists interface.

1. To [add items in CSV format](/firewall/cf-dashboard/rules-lists/manage-items/#add-items-in-csv-format), select **Upload CSV**.

### Add items to a list manually

1. In the **Add items to list** page, add an IP address and an optional description in the text inputs.

    As you enter information into a text input, a new row of inputs displays below the current one. To delete any of the IP addresses that you have entered, select **X**.

1. Select **Add to list**.

### Add items in CSV format

{{<Aside type="warning" header="Important">}}

Importing a CSV file to a list only updates descriptions or adds items to the list. It does not delete items from a list.

If you need to replace the entire contents of a list, format the data as an array and use the Update all list items operation in the [Lists API](/firewall/api/cf-lists/endpoints/).

{{</Aside>}}

#### Use valid CSV file format

When uploading a CSV file containing a list of IP addresses and optional descriptions, be sure that each item is on its own line, as in this example:

```txt
<IP_ADDRESS_1>,<DESCRIPTION_1>
<IP_ADDRESS_2>
```

#### Upload a CSV file

To add items to an IP List by uploading a CSV file:

1. In the **Add items to list** page, select **Upload CSV**.

2. Browse to the location of the CSV file, select the file, and then select **Open**. The displayed items in the page will include the items loaded from the CSV file.

3. You can continue to edit the items in the list before adding them:

    - To delete any of the IP addresses that you have entered, select **X**.
    - To add extra IP addresses manually, enter the information in the text inputs.

4. Select **Add to list**.

{{<Aside type="warning" header="Important">}}

When uploading CSV data, keep in mind that duplicate data is treated as follows:

- IP addresses that were already in the list are updated with the description from the CSV file.
- IP addresses in the CSV file that were not already in the list are added to the list.

{{</Aside>}}

## Delete items from a list

1. [Access the Lists interface](/firewall/cf-dashboard/rules-lists/) available at **Manage Account** > **Configurations** > **Lists**.

2. Select **Edit** next to the list from which you want to delete items.

3. Select the checkboxes next to the items you want to delete. To select all the items, use the checkbox in the column header:

    ![Selecting individual list items to delete from an IP List](/firewall/static/lists-delete-items.png)

4. Select **Remove**.

5. In the confirmation dialog, select **Remove** to complete the operation.
