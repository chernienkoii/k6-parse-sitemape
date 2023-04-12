import http from 'k6/http';
import { sleep } from 'k6';
import { parseHTML } from 'k6/html';

const sitemapContents = open('sitemap2.xml');

const doc = parseHTML(sitemapContents);
const urls = doc.find('url > loc').toArray().map((node) => node.text());

export let options = {
  vus: 50, // number of virtual users to simulate
  duration: '60m', // duration of the test in seconds
};

export default function () {
  const url = urls[Math.floor(Math.random() * urls.length)];
  const res = http.get(url);
  console.log(`Response time for ${res.url}: ${res.timings.duration} ms`);
  sleep(1); // wait for 1 second between requests
}
