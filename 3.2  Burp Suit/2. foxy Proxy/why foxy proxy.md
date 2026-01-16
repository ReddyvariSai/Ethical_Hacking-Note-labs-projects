# Burp Suite

In Burp Suite, Foxy Proxy is a browser extension used to manage and redirect web traffic through the Burp Suite proxy server. It acts as a switch that allows you to route your browsing data to Burp Suite so you can intercept and analyze requests before they reach the internet.

## Why Foxy Proxy is Used

* Man-in-the-Middle Setup: Normally, a browser connects directly to the internet. By using Foxy Proxy, the browser is instructed to send all traffic to Burp Suite first, which then passes it to the internet, allowing the tester to see and modify the data in transit.
* Convenience and Efficiency: Changing proxy settings manually in browser menus is a "laggy" and repetitive process. Foxy Proxy allows you to toggle the proxy on and off with a single click from the browser toolbar.
* Encrypted Traffic (HTTPS): When Foxy Proxy is enabled and a CA certificate is imported, it allows the tester to intercept secure HTTPS requests that would otherwise be hidden or blocked by the browser.

<img width="1506" height="915" alt="image" src="https://github.com/user-attachments/assets/438ad771-803d-450a-80c8-700fa37b63b7" />

<img width="1505" height="875" alt="image" src="https://github.com/user-attachments/assets/4cfb3218-4248-4f14-9c2c-3faa6ea2b45f" />

## How it is Configured

* Host and Port: Foxy Proxy is typically configured to point to the loopback IP address 127.0.0.1 using port 8080, which is the default proxy listener for Burp Suite.
* Visual Indicators: Testers can assign specific colors to proxy profiles; for example, when the proxy is enabled, the icon may change to green to indicate that traffic is being successfully routed through Burp.
* Browser Choice: While modern versions of Burp Suite include a built-in Chromium browser that doesn't require setup, many professionals prefer using Firefox with Foxy Proxy because it is considered "handy" and easy to configure for web assessments.

By utilizing Foxy Proxy, you ensure that every part of the web communication including headers, parameters, and cookies—is captured by Burp Suite for detailed security testing.

## How to Setup FoxyProxy on Firefox?

FoxyProxy is a powerful browser extension that simplifies the process of using proxies with Google Chrome and Firefox. It allows users to easily manage proxy settings, switch between multiple proxies, and route traffic through specific proxies based on URL patterns, all from a simple interface. This extension is especially useful for users who need flexibility and control over their proxy configurations, whether for privacy, bypassing geo-restrictions, or testing network settings.

In this article, we'll guide you step-by-step through the process of setting up FoxyProxy on both Google Chrome and Firefox.
Setting up FoxyProxy on Firefox

Follow these steps to install and configure FoxyProxy on Firefox:
1. Install the FoxyProxy extension

* Open Firefox, visit the Firefox Add-ons website and search for the FoxyProxy Standard extension.

<img width="1600" height="501" alt="image" src="https://github.com/user-attachments/assets/e810b16e-e441-4247-ba09-04f1f1b62218" />

Click Add to Firefox, then click Add in the confirmation prompt

<img width="1600" height="581" alt="image" src="https://github.com/user-attachments/assets/29dec6c6-a30c-45e5-92d2-f0a106bf89bf" />

2. Access the FoxyProxy icon

  *  After installation, the FoxyProxy icon will appear in the Firefox toolbar.
  * If you don’t see it, click the menu button (three horizontal lines) and go to Add-ons and Themes to find FoxyProxy and manage its settings.

3. Open the FoxyProxy settings

  *  Click the FoxyProxy icon in the toolbar and select Options to open the settings page.

<img width="437" height="502" alt="image" src="https://github.com/user-attachments/assets/00f6a834-8b73-4600-9e77-511557469adf" />

4. Add a new proxy

* On the Proxies tab, click the Add button and fill in the necessary details, as discussed above. If you do not have proxies, get 10 for free from Webshare.
*  Click Save to store your proxy settings.

<img width="1548" height="605" alt="image" src="https://github.com/user-attachments/assets/63324abc-24a9-485c-ab1b-8cb0dd52c60a" />

5. Activate the proxy

  *  After saving, go back to the FoxyProxy main page and enable the proxy by selecting it from the dropdown list.

<img width="1539" height="920" alt="image" src="https://github.com/user-attachments/assets/1e181483-9f39-4749-b938-a8e4375d8718" />


# Setting up FoxyProxy on Google Chrome

Follow these steps to install and configure FoxyProxy on Google Chrome:

1. Install the FoxyProxy extension
 
 * Open Google Chrome and visit the Chrome Web Store.
* In the search bar, type FoxyProxy and press Enter.
* Select FoxyProxy Standard from the search results.
* Click Add to Chrome and then Add Extension in the confirmation dialog

2. Access the FoxyProxy icon

  *  After installation, you’ll notice the FoxyProxy icon (a fox head) in the Chrome toolbar.
   * If you don’t see it, click the Extensions menu and pin FoxyProxy to the toolbar for easier access.

3. Open the FoxyProxy settings

  *  Click the FoxyProxy icon in the toolbar to open the extension menu.
  *  From the dropdown, click Options to access the settings page.

4. Add a new proxy

 * On the FoxyProxy options page, go to the Proxies tab and click the Add button.

    In the dialog that appears, you'll need to fill in the following fields:some text
      *  Title: Give your proxy a name (e.g., "Test-Proxy").
      *  Type: Select the proxy type (HTTP, HTTPS, SOCKS, etc.).
      *  Hostname: Enter the proxy server's IP address or hostname.
      *  Port: Provide the port number for the proxy.
      *  Username/Password: If authentication is required, enter your proxy credentials.
   * You can find your proxy server details in your Webshare account after signing up for their free proxies.
5. Save and activate the proxy

 *   Once you’ve entered all the proxy details, click Save to store the configuration.
* Back on the main Options page, enable the proxy by selecting it from the dropdown list.

6. Set proxy rules (optional)

   * To create custom rules for routing traffic through your proxy, click on the Pattern Tester tab.
   * Define URL patterns for specific websites to automatically route them through the selected proxy, leaving other traffic unaffected.

# Wrapping up: setting up FoxyProxy in Chrome and Firefox

With FoxyProxy, managing proxies becomes a simple and efficient process. Whether you're using it for enhanced privacy, accessing geo-blocked content, or managing multiple IP addresses for various tasks, FoxyProxy streamlines the process across both Chrome and Firefox. By following the steps in this guide, you can seamlessly integrate FoxyProxy into your browsing experience, offering enhanced control and flexibility.



























