### Upton
---
https://github.com/propublica/upton

```
gem 'upton'


```

```ruby
scraper = Upton::Scraper.new("http://www.propublica.org", "section#river h1 a")
scraper.scrape_to_csv "outpub.csv" do |html|
  Nokogiri::HTML(html).search("#comments h2.title-link").map &:text
end

scraper = Upton::Scraper.new("http://www.propublica.org", "section#river section h1 a")
scraper.scrape do |article_html_string|
  puts "here is the full html content of the ProPublica article listed on the homepage: "
  puts "#{article_html_string}"
end

scraper = Upton::Scraper.new("http://www.propublica.org/search/search.php?q=tools", ".compact-list a.title-link")
scraper.paginated = true
scraper.pagination_param = 'p'
scraper.pagination_max_pages = 3
scraper.scrape_to_csv("output.csv", &Upton::Utils.list("h2"))
```

```
```
