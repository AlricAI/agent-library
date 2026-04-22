# EXAMPLES

> This document provides practical examples of how to use and customize the web scraping workflow for different scenarios.

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Web Scraping Workflow Examples

This document provides practical examples of how to use and customize the web scraping workflow for different scenarios.

## Example 1: Scraping Blog Articles

This example demonstrates how to scrape blog posts from a website and extract the title, author, date, and content.

### Initial Configuration

```javascript
// Input data for the workflow
{
  "url": "https://example-blog.com/posts",
  "baseUrl": "https://example-blog.com/posts",
  "currentPage": 1,
  "maxPages": 5
}
```

### CSS Selectors

```javascript
// HTML Extract node configuration
{
  "extractionValues": {
    "values": [
      {
        "key": "postTitle",
        "cssSelector": "h2.post-title",
        "returnArray": false
      },
      {
        "key": "postAuthor",
        "cssSelector": "span.author-name",
        "returnArray": false
      },
      {
        "key": "postDate",
        "cssSelector": "time.published-date",
        "returnArray": false
      },
      {
        "key": "postContent",
        "cssSelector": "div.post-content",
        "returnArray": false
      }
    ]
  }
}
```

### Pagination Detection

```javascript
// Function node to detect the last page
{
  "functionCode": `
    // Check if there's a "Next" button
    const hasNextPage = $json.hasNextButton !== null && $json.hasNextButton !== undefined;
    
    // Check if we've reached the maximum pages
    const reachedMaxPages = $json.currentPage >= $json.maxPages;
    
    // Determine if we're done
    $json.areWeDone = !hasNextPage || reachedMaxPages;
    
    return $json;
  `
}
```

## Example 2: E-commerce Product Scraping

This example shows how to scrape product information from an e-commerce website.

### Initial Configuration

```javascript
// Input data for the workflow
{
  "url": "https://example-store.com/products",
  "baseUrl": "https://example-store.com/products",
  "currentPage": 1,
  "maxPages": 10,
  "category": "electronics"
}
```

### CSS Selectors

```javascript
// HTM

*[truncated — see source for full prompt]*