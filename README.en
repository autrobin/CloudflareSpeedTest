XIU2/CloudflareSpeedTest

Go Version Release Version GitHub License GitHub Star GitHub Fork

Many international websites use Cloudflare CDN, but the IPs assigned to visitors from mainland China are not user-friendly (high latency, high packet loss, slow speed).

Although Cloudflare publishes all IP ranges, finding the right one from so many can be incredibly difficult. That's why this software was created.

"Select Your Best IP" to test Cloudflare CDN latency and speed, and get the fastest IP (IPv4+IPv6)! If you find it useful, please give it a ⭐ to show your support!

Sharing my other open-source projects: TrackersList.com - A list of popular BT Trackers across the web! Effectively improve BT download speed~

UserScript - 🐵 Over a dozen Tampermonkey scripts including high-speed Github download, Zhihu enhancement, automatic seamless page turning, eye protection mode, etc.

SNIProxy - 🧷 A simple SNI proxy for personal use (supports all platforms, all systems, front-end proxy, easy configuration, etc.)

Of course, this project also supports latency testing for websites with other CDNs/multiple DNS IPs, but you need to find the corresponding download speed test addresses yourself.

Important

Cloudflare CDN explicitly prohibits the use of proxy methods. Those using proxies with CDNs assume all risks and should not rely excessively on them. #382 #383

# Quick Start
Download and Run
Download the compiled executable file (Github Releases/Lanzou Cloud) and extract it.
Double-click to run the cfst.exe file (Windows system), wait for the speed test to complete...

"Click to view other installation methods under Windows system"

"Click to view usage examples under Linux system"
Run CFST independently on your mobile phone Simple Speed ​​Test Tutorial: Android, Android App, iOS

Note

Attention! This software is only for websites and does not support selecting the best IP for Cloudflare WARP using the UDP protocol. See: #392 for details.

Result Example After the speed test is complete, the 10 fastest IPs will be displayed by default. Example (output example only):

IP ​​Address Sent Received Packet Loss Rate Average Latency Download Speed ​​(MB/s) Region Code

104.27.200.69 4 4 0.00 146.23 28.64 LAX

172.67.60.78 4 4 0.00 139.82 15.02 SEA

104.25.140.153 4 4 0.00 146.49 14.90 SJC

104.27.192.65 4 4 0.00 140.28 14.07 LAX
172.67.62.214 4 0.00 139.29 12.71 LAX
104.27.207.5 4 4 0.00 145.92 11.95 LAX
172.67.54.193 4 4 0.00 146.71 11.55 LAX
104.22.66.8 4 4 0.00 147.42 11.11 SEA
104.27.197.63 4 4 0.00 131.29 10.26 FRA
172.67.58.91 4 4 0.00 140.19 9.14 SJC
...

# If the average latency is very low (e.g., 0.xx), it indicates that CFST speed testing used a proxy. Please close the proxy software before testing.

# If running on a router, please close (or exclude) the proxy within the router; otherwise, the speed test results may be inaccurate or unusable.

# Because each speed test uses a random IP within each IP range, the results will vary each time, which is normal!

# Note! I found that the latency is significantly higher during the first speed test after booting up (manual TCPing also shows this), but subsequent tests are normal.

# Therefore, it is recommended that before the first official speed test after booting up, you test a few random IPs (no need to wait for the latency test to complete; you can close it as soon as the progress bar moves).

# The approximate steps of the software's process under default parameters:

# 1. Latency test (default TCPing mode; HTTPing mode requires manual parameter addition)

# 2. Latency sorting (latency is sorted from low to high and filtered by conditions; different packet loss rates are sorted separately, so there may be some IPs with low latency but packet loss). (Place at the end)

# 3. Download Speed ​​Test (Starts with the IP with the lowest latency and tests download speeds sequentially, stopping after 10 tests by default)

# 4. Speed ​​Sort (Sort by speed from highest to lowest)

# 5. Output Results (Control whether to output to the command line (-p 0) or to a file (-o "") via parameters)

# Note: The output result file result.csv will display garbled Chinese characters when opened with Microsoft Excel, which is normal. Other spreadsheet software/Notepad will display it correctly. The first line of the speed test results shows the fastest IP with both the fastest download speed and the lowest average latency!

The complete results are saved in the result.csv file in the current directory. Open it with Notepad/spreadsheet software. The format is as follows:

IP ​​Address, Sent, Received, Packet Loss Rate, Average Latency, Download Speed ​​(MB/s), Region Code

104.27.200.69,4,4,0.00,146.23,28.64,LAX

Note
If you find that the download speed is... If the download speed is 0.00, you can use debug mode (-debug) to investigate. See: # Download speed test results are all 0.00?

You can further filter the complete results according to your needs, or check out the advanced usage with specified filtering conditions!

# Advanced Usage Running this directly uses the default parameters. If you want more comprehensive speed test results that better meet your requirements, you can customize the parameters.

C:\>cfst.exe -h

CloudflareSpeedTest vX.X.X Tests the latency and speed of all IPs on various CDNs or websites to get the fastest IP (IPv4+IPv6)!

https://github.com/XIU2/CloudflareSpeedTest

Parameters:

-n 200
Latency test threads; the more threads, the faster the latency test. Do not set too high for devices with weak performance (such as routers); (default 200, maximum 1000)

-t 4
Latency test count; the number of latency tests for a single IP; (default 4) -dn 10

Number of download speed tests; After delay testing and sorting, the number of download speed tests will be performed starting from the lowest latency; (default 10)

-dt 10

Download speed test time; Maximum download speed test time for a single IP address, cannot be too short; (default 10 seconds)

-tp 443

Specify the speed test port; The port used for delay/download speed tests; (default port 443)

-url https://cf.xiu2.xyz/url

Specify the speed test address; The address used for delay (HTTPing)/download speed tests. The default address is not guaranteed to be available; it is recommended to build your own.

When performing a download speed test, the software will obtain the current region code of the IP address from the HTTP response header (supports Cloudflare, AWS CloudFront, Fastly, Gcore, CDN77, Bunny, etc.) and display it.

-httping

Switch the speed test mode; Change the delay speed test mode to HTTP protocol, and the test address used is the [-url] parameter; (default) (TCPing)

When using HTTP speed test mode, the software retrieves the current region code of the IP address from the HTTP response header (supports Cloudflare, AWS CloudFront, Fastly, Gcore, CDN77, Bunny, and other CDNs) and displays it.

Note: HTTPing is essentially a network scanning behavior. Therefore, if you are running it on a server, you need to reduce concurrency (-n), otherwise some strict providers may suspend your service.

If you encounter a situation where the number of available IPs is normal in the first HTTPing speed test, but the number decreases or even drops to 0 in subsequent tests, but recovers after a period of inactivity, it may be because your ISP or Cloudflare CDN considers you to be performing a network scan and triggers a temporary restriction mechanism. It is recommended to reduce concurrency (-n) to reduce the occurrence of this situation.

-httping-code 200

Valid status code; the valid HTTP status code returned by the webpage during HTTPing latency testing, limited to one; (default 200 301 302)

-cfcolo HKG, KHH, NRT, LAX, SEA, SJC, FRA, MAD

Matches a specified region; IATA airport area code or country/city code, comma-separated, case-insensitive, only available in HTTPing mode; (default: all regions)

Supports Cloudflare, AWS CloudFront, Fastly, Gcore, CDN77, Bunny, and other CDNs.

Cloudflare, AWS CloudFront, and Fastly use three-letter IATA airport area codes, such as HKG, LAX.

CDN77 and Bunny use two-letter country/region codes, such as US, CN.

Gcore uses two-letter city codes, such as FR, AM.

Therefore, when using -cfcolo to specify a region code, you must specify a different type of region code according to the different CDNs.

-tl 200

Average latency limit; only outputs IPs with latency lower than the specified average latency. Various upper and lower limits can be used in combination; (default: 9999 ms)

-tll 40

Average latency lower limit; only outputs IPs with a latency higher than the specified average latency; (default 0 ms)

-tlr 0.2

Packet loss probability upper limit; only outputs IPs with a packet loss rate lower than or equal to the specified packet loss rate, ranging from 0.00 to 1.00. 0 filters out any IPs with packet loss; (default 1.00)

-sl 5

Download speed lower limit; only outputs IPs with a download speed higher than the specified download speed. The speed test will stop only after a specified number of IPs are reached [-dn]; (default 0.00 MB/s)

-p 10
Number of results to display; directly displays the specified number of results after the speed test. 0 results are displayed and the test exits directly; (default 10)

-f ip.txt
IP range data file; please add quotes if the path contains spaces; supports other CDN IP ranges; (default ip.txt)

-ip 1.1.1.1,2.2.2.2/24,2606:4700::/32
Specify IP range data; directly specify the IP range data to be tested via parameters, separated by commas; (default empty)

-o result.csv

Write the results to the file; if the path contains spaces, please add quotation marks; if the value is empty, it will not be written to the file [-o ""]; (default result.csv)

-dd
Disable download speed test; after disabling, the speed test results will be sorted by latency (default sorted by download speed); (default enabled)

-allip
Test all IPs; test the speed of each IP in the IP range (IPv4 only); (default randomly tests one IP per /24 range)

-debug
Debug output mode; will output more logs in some unexpected situations to help determine the cause; (default off)

Currently, this function only applies to the HTTPing latency speed test process and the download speed test process. If the speed test of the current IP is interrupted for various reasons during the process, an error reason will be output.

For example: during the HTTPing latency speed test, the speed test is terminated due to an incorrect HTTP status code, a problem with the speed test address, or a timeout.

For example, during the download speed test, the download speed test address may have issues (blocked, 403 status code, timeout, etc.).
