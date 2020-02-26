# WebScraper

Look at https://blog.hartleybrody.com/web-scraping-cheat-sheet/ for help

Current file: Web_crawler, old copy: SearchEngine

For now: loop to get links then loop on that to save them, when robots.txt works we can put everything together in one loop.

Note that links are saved inside folder Documents_craled in the crawler's repository, here saved inside data folder.


## Obsolete pseudocode

Pseudocode for getting contents of link:
We have: a link to get contents of, its root, its robots.txt file and 
l_servers: list of (server name, crawl_delay) (where crawl_delay = 20ms by default)

if link's server is in l_servers: wait for (crawl_delay time)

if ("User-agent: \*" not in robots.txt): get full contents
else:
    line = 1st line under "User-agent: \*"
    if ("User agent:\* \n Allow: \" in robots.txt; or "Allow: \" in line): get full contents of link
    if ("User agent:\* \n Disallow: \" in robots.txt; or "Disallow: \" in line): break
    else:
        while ("Allow" in line) | ("Disallow" in line):
            if "Allow" in line:
                s = root + line - "Allow: "
                if s in link: get full contents of link
            if "Disallow" in line: 
                s = root + line - "Disallow: "
                if s in link: break
            line = next line
        # If we have reached end of specifications for crawlers without explicit allowance or disallowance for our
        # url: get full contents 
        if ("Allow" not in line) & ("Disallow" not in line):
            get full contents of link
