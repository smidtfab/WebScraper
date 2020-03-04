# WebScraper

Look at https://blog.hartleybrody.com/web-scraping-cheat-sheet/ for help

Current file: Web_crawler, old copy: SearchEngine

For now: loop to get links then loop on that to save them, when robots.txt works we can put everything together in one loop.

Note that links are saved inside folder Documents_craled in the crawler's repository, here saved inside data folder.


## Pseudocode for big, final function:

Pseudocode: Crawler (nb_max_url, [URL], Domains, Links):

Get robots.txt url + domain 
Save domain, robots.txt url and crawl delay if don't already have it

If can fetch: 

    If domain in domains & time crawled > 0:
        Wait max(0, crawl delay - (current time - time crawled))
    
    Crawl: save contents 
    Update time crawled
    Save links if we still need more
    Save in matrix domains line: domain, crawl delay (20ms if none), time crawled

If haven't crawled enough links: repeat
    
Links = list of links we can crawl
Domains: [domain, robots.txt link, crawl delay, time last crawled]
(several links can have same domain)

Auxiliary functions: extract up to M links from a page, new filename, save a link

To be able to **wait for crawler delay time**, need functions get current time, wait a certain time (need to know units of said time!!!)
