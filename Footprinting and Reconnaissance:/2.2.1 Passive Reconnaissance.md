# Passive Reconnaissance

Welcome to the first room of the Network Security Module. This module covers:

1. Passive Reconnaissance
2. Active Reconnaissance
3. Nmap Live Host Discovery
4. Nmap Basic Port Scans
5. Nmap Advanced Port Scans
6. Nmap Post Port Scans
7. Protocols and Servers
8. Protocols and Servers 2
9. Network Security Challenge

In this room, after we define passive reconnaissance and active reconnaissance, we focus on essential tools related to passive reconnaissance. We will learn three command-line tools:

`whois `to query WHOIS servers

`nslookup` to query DNS servers

`dig` to query DNS servers

We use `whois` to query WHOIS records, while we use `nslookup` and `dig` to query DNS database records. These are all publicly available records and hence do not alert the target.

We will also learn the usage of two online services:

DNSDumpster
Shodan.io
These two online services allow us to collect information about our target without directly connecting to it.

Pre-requisites: This room requires basic networking knowledge along with basic familiarity with the command line. The modules Network Fundamentals and Linux Fundamentals provide the required knowledge if necessary.

# Whois 

WHOIS is a request and response protocol that follows the RFC 3912 specification. A WHOIS server listens on TCP port 43 for incoming requests. The domain registrar is responsible for maintaining the WHOIS records for the domain names it is leasing. The WHOIS server replies with various information related to the domain requested. Of particular interest, we can learn:

1. Registrar: Via which registrar was the domain name registered?
2. Contact info of registrant: Name, organization, address, phone, among other things. (unless made hidden via a privacy service)
3. Creation, update, and expiration dates: When was the domain name first registered? When was it last updated? And when does it need to be renewed?
4. Name Server: Which server to ask to resolve the domain name?

To get this information, we need to use a `whois` client or an online service.
Many online services provide whois information; however, it is generally faster and more convenient to use your local whois client.
Using the AttackBox (or your local Linux machine, such as Parrot or Kali), you can easily access your whois client on the terminal.
The syntax is `whois DOMAIN_NAME`, where `DOMAIN_NAME` is the domain about which you are trying to get more information. Consider the following example executing `whois tryhackme.com`.

We can see plenty of information; we will inspect them in the order displayed. First, we notice that we were redirected to whois.namecheap.com to get our information. In this case and at the time being, namecheap.com is maintaining the WHOIS record for this domain name. Furthermore, we can see the creation date along with the last-update date and expiration date.

Next, we obtain information about the registrar and the registrant. We can find the registrant’s name and contact information unless they are using some privacy service. Although not displayed above, we get the admin and tech contacts for this domain. Finally, we see the domain name servers that we should query if we have any DNS records to look up.

The information collected can be inspected to find new attack surfaces, such as social engineering or technical attacks. For instance, depending on the scope of the penetration test, you might consider an attack against the email server of the admin user or the DNS servers, assuming they are owned by your client and fall within the scope of the penetration test.

It is important to note that due to automated tools abusing WHOIS queries to harvest email addresses, many WHOIS services take measures against this. They might redact email addresses, for instance. Moreover, many registrants subscribe to privacy services to avoid their email addresses being harvested by spammers and keep their information private.

On the AttackBox, open the terminal and run the whois tryhackme.com command to get the information you need to answer the following questions.


# nslookup & dig

In the previous task, we used the WHOIS protocol to get various information about the domain name we were looking up. In particular, we were able to get the DNS servers from the registrar.

Find the IP address of a domain name using `nslookup`, which stands for Name Server Look Up. You need to issue the command `nslookup DOMAIN_NAME`, for example, `nslookup tryhackme.com`. Or, more generally, you can use `nslookup OPTIONS DOMAIN_NAME SERVER`. These three main parameters are:

1. OPTIONS contains the query type as shown in the table below. For instance, you can use `A` for IPv4 addresses and `AAAA` for IPv6 addresses.
2. DOMAIN_NAME is the domain name you are looking up.
3. SERVER is the DNS server that you want to query. You can choose any local or public DNS server to query. Cloudflare offers `1.1.1.1` and `1.0.0.1`, Google offers `8.8.8.8` and `8.8.4.4`, and Quad9 offers `9.9.9.9` and `149.112.112.112`. There are many more public DNS servers that you can choose from if you want alternatives to your ISP’s DNS servers.


<img width="861" height="583" alt="image" src="https://github.com/user-attachments/assets/09973963-15aa-4ae5-83b3-e50de055e3d1" />

For instance, `nslookup -type=A tryhackme.com 1.1.1.1` (or `nslookup -type=a tryhackme.com 1.1.1.1` as it is case-insensitive) can be used to return all the IPv4 addresses used by tryhackme.com

The A and AAAA records are used to return IPv4 and IPv6 addresses, respectively. This lookup is helpful to know from a penetration testing perspective. In the example above, we started with one domain name, and we obtained three IPv4 addresses. Each of these IP addresses can be further checked for insecurities, assuming they lie within the scope of the penetration test.

Let’s say you want to learn about the email servers and configurations for a particular domain. You can issue `nslookup -type=MX tryhackme.com`.

We can see that tryhackme.com’s current email configuration uses Google. Since MX is looking up the Mail Exchange servers, we notice that when a mail server tries to deliver email `@tryhackme.com`, it will try to connect to the `aspmx.l.google.com`, which has order 1. If it is busy or unavailable, the mail server will attempt to connect to the next in order mail exchange servers, `alt1.aspmx.l.google.com` or` alt2.aspmx.l.google.com`.

Google provides the listed mail servers; therefore, we should not expect the mail servers to be running a vulnerable server version. However, in other cases, we might find mail servers that are not adequately secured or patched.

Such pieces of information might prove valuable as you continue the passive reconnaissance of your target. You can repeat similar queries for other domain names and try different types, such as `-type=txt`. Who knows what kind of information you might discover along your way!

For more advanced DNS queries and additional functionality, you can use `dig`, the acronym for “Domain Information Groper,” if you are curious. Let’s use dig to look up the MX records and compare them to `nslookup`. We can use `dig DOMAIN_NAME`, but to specify the record type, we would use `dig DOMAIN_NAME TYPE`. Optionally, we can select the server we want to query using `dig @SERVER DOMAIN_NAME TYPE`.

1. SERVER is the DNS server that you want to query.
2. DOMAIN_NAME is the domain name you are looking up.
3. TYPE contains the DNS record type, as shown in the table provided earlier.


A quick comparison between the output of `nslookup` and dig shows that dig returned more information, such as the TTL (Time To Live) by default. If you want to query a `1.1.1.1` DNS server, you can execute `dig @1.1.1.1 tryhackme.com MX`.

Using the AttackBox, open the terminal and use the `nslookup` or dig command to get the information you need to answer the following question.


# DNSDumpster


DNS lookup tools, such as nslookup and dig, cannot find subdomains on their own. The domain you are inspecting might include a different subdomain that can reveal much information about the target. For instance, if tryhackme.com has the subdomains wiki.tryhackme.com and webmail.tryhackme.com, you want to learn more about these two as they can hold a trove of information about your target. There is a possibility that one of these subdomains has been set up and is not updated regularly. Lack of proper regular updates usually leads to vulnerable services. But how can we know that such subdomains exist?

We can consider using multiple search engines to compile a list of publicly known subdomains. One search engine won’t be enough; moreover, we should expect to go through at least tens of results to find interesting data. After all, you are looking for subdomains that are not explicitly advertised, and hence it is not necessary to make it to the first page of search results. Another approach to discover such subdomains would be to rely on brute-forcing queries to find which subdomains have DNS records.

To avoid such a time-consuming search, one can use an online service that offers detailed answers to DNS queries, such as DNSDumpster. If we search DNSDumpster for tryhackme.com, we will discover the subdomain blog.tryhackme.com, which a typical DNS query cannot provide. In addition, DNSDumpster will return the collected DNS information in easy-to-read tables and a graph. DNSDumpster will also provide any collected information about listening servers.

We will search for tryhackme.com on DNSDumpster to give you a glimpse of the expected output. Among the results, we got a list of DNS servers for the domain we are looking up. DNSDumpster also resolved the domain names to IP addresses and even tried to geolocate them. We can also see the MX records; DNSDumpster resolved all five mail exchange servers to their respective IP addresses and provided more information about the owner and location. Finally, we can see TXT records. Practically a single query was enough to retrieve all this information.


 <img width="1420" height="1080" alt="image" src="https://github.com/user-attachments/assets/d5f759b3-0b65-4db7-babf-16bf354b4921" />

DNSDumpster will also represent the collected information graphically. DNSDumpster displayed the data from the table earlier as a graph. You can see the DNS and MX branching to their respective servers and also showing the IP addresses.


<img width="2482" height="799" alt="image" src="https://github.com/user-attachments/assets/ab2fc461-d5a4-45fd-a002-3a295fb85822" />

There is currently a beta feature that allows you to export the graph as well. You can manipulate the graph and move blocks around if needed.


<img width="2913" height="3757" alt="image" src="https://github.com/user-attachments/assets/84ea123f-ec7b-4012-aabe-1130f6aa3cef" />

# Shodan.io

When you are tasked to run a penetration test against specific targets, as part of the passive reconnaissance phase, a service like Shodan.io can be helpful to learn various pieces of information about the client’s network, without actively connecting to it. Furthermore, on the defensive side, you can use different services from Shodan.io to learn about connected and exposed devices belonging to your organization.

Shodan.io tries to connect to every device reachable online to build a search engine of connected “things” in contrast with a search engine for web pages. Once it gets a response, it collects all the information related to the service and saves it in the database to make it searchable. Consider the saved record of one of tryhackme.com’s servers.


<img width="1252" height="572" alt="image" src="https://github.com/user-attachments/assets/09d7ff44-9cfe-4ba4-8936-c008ea13899c" />

This record shows a web server; however, as mentioned already, Shodan.io collects information related to any device it can find connected online. Searching for tryhackme.com on Shodan.io will display at least the record shown in the screenshot above. Via this Shodan.io search result, we can learn several things related to our search, such as:

1. IP address
2. hosting company
3. geographic location
4. server type and version
You may also try searching for the IP addresses you have obtained from DNS lookups. These are, of course, more subject to change. On their help page, you can learn about all the search options available at Shodan.io, and you are encouraged to join TryHackMe’s Shodan.io.

It would be best to visit Shodan.io to answer the following questions; however, note that you can find the answers on Shodan.io without needing a premium account.


In this room, we focused on passive reconnaissance. In particular, we covered command-line tools, whois, nslookup, and dig. We also discussed two publicly available services DNSDumpster and Shodan.io. The power of such tools is that you can collect information about your targets without directly connecting to them. Moreover, the trove of information you may find using such tools can be massive once you master the search options and get used to reading the results.


<img width="856" height="665" alt="image" src="https://github.com/user-attachments/assets/25e5dd3e-670f-41cc-8974-5b405260597f" />






