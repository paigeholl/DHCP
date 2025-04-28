# 6. Set up a DHCP Server

## Overview

Setting up a DHCP (Dynamic Host Configuration Protocol) server allows Windows 10 clients to automatically receive IP addresses with specified lease times, enabling them to connect to the internet without manual configuration.

## Installation Steps

1. In Server Manager, select **Add roles and features**

<img src=https://ik.imagekit.io/typeai/tr:w-1200,c-at_max/img_EFKNZUItLV27DBv5F8.png width=400px>

2. Click **Next** through the wizard until you reach the server selection screen, verify the correct server is selected, then click **Next**.

<img src=https://ik.imagekit.io/typeai/tr:w-1200,c-at_max/img_iYZcsCxNZmYh1ujXFy.png width=400px>

3. Select **DHCP Server** from the roles list. When the popup appears, click **Add Features**.

<img src=https://ik.imagekit.io/typeai/tr:w-1200,c-at_max/img_xA1zY7kdf3sVhGiIhU.png width=400px>

4. Continue clicking **Next** through the remaining screens until you reach the Confirmation page, then click **Install**.
5. After installation completes, click **Close**.
6. To configure DHCP, click **Tools** > **DHCP** in Server Manager.

<img src=https://ik.imagekit.io/typeai/tr:w-1200,c-at_max/img_v4UfHOXlXwfeqBNQgl.png width=400px>

## Creating a DHCP Scope

1. In the DHCP console, expand the Domain Controller node, right-click on **IPv4**, and select **New Scope...**.

<img src=https://ik.imagekit.io/typeai/tr:w-1200,c-at_max/img_q3AqPdd2iGZfxcLoJU.png width=400px>

2. When the New Scope Wizard appears, click **Next**.
3. Enter a descriptive name for the scope (typically based on the IP range), then click **Next**.

<img src=https://ik.imagekit.io/typeai/tr:w-1200,c-at_max/img_4BQgKms2oIwQq10ChW.png width=400px>

4. Define the IP address range:
   - Enter the **Start IP address** and **End IP address**
   - Set the **Subnet mask** to `/24` (255.255.255.0)
   - Click **Next**

<img src=https://ik.imagekit.io/typeai/tr:w-1200,c-at_max/img_5eFf8U03NZi5RNwflq.png width=400px>

5. On the exclusions screen, click **Next** (we don't need to exclude any IPs in this configuration).

<img src=https://ik.imagekit.io/typeai/tr:w-1200,c-at_max/img_qsYtwbqUCAqKFSnlUk.png width=400px>

6. Configure the lease duration:
   - For most networks, the default duration is appropriate
   - For high-traffic environments (like coffee shops), consider shorter lease times (1 hour or less)
   - Long lease times can tie up IP addresses unnecessarily when clients disconnect

<img src=https://ik.imagekit.io/typeai/tr:w-1200,c-at_max/img_8hCzmqEh5WvdX50mnn.png width=400px>

7. When asked to configure DHCP options, select **Yes** and click **Next**. This allows you to specify DNS servers and the default gateway for clients.

<img src=https://ik.imagekit.io/typeai/tr:w-1200,c-at_max/img_wZ2EqIMfSDa7zVoqYt.png width=400px>

8. Enter your gateway IP address, click **Add**, then continue clicking **Next** until you reach the completion page, then click **Finish**.

<img src=https://ik.imagekit.io/typeai/tr:w-1200,c-at_max/img_zIs4GwdzXKsq3SX6tH.png width=400px>

## Activating the DHCP Server

If the IPv4 and IPv6 icons don't turn green automatically:

1. Right-click on the server domain
2. Select **Authorize**
3. Click **Refresh**

<img src=https://ik.imagekit.io/typeai/tr:w-1200,c-at_max/img_KA1u3RYLEHcVsJoJ5q.png width=400px>

## Configuring Internet Access on the Domain Controller (Lab Environments Only)

> **Note**: This section is for lab environments only. These steps are not recommended for production environments.

1. Click on **Configure this local server** in Server Manager.

<img src=https://ik.imagekit.io/typeai/tr:w-1200,c-at_max/img_uccE1HgBYoJLK1E7IO.png width=400px>

2. Locate the IE Enhanced Security Configuration setting (showing as "On").
3. Click on the "On" link and turn off the security configuration for both Administrators and Users.

<img src=https://ik.imagekit.io/typeai/tr:w-1200,c-at_max/img_gq4kdc3rkW1kdvpv4K.png width=400px>

<img src=https://ik.imagekit.io/typeai/tr:w-1200,c-at_max/img_TGMBD2SHkdIe3Qdk2J.png width=400px>

