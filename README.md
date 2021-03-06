# yts-api-pt

[![Build Status](https://travis-ci.org/ChrisAlderson/yts-api-pt.svg?branch=master)]()
[![Dependency Status](https://david-dm.org/ChrisAlderson/yts-api-pt.svg)](https://david-dm.org/ChrisAlderson/yts-api-pt)
[![devDependency Status](https://david-dm.org/ChrisAlderson/yts-api-pt/dev-status.svg)](https://david-dm.org/ChrisAlderson/yts-api-pt#info=devDependencies)

A NodeJS wrapper for [yts.ag](https://yts.ag/).

## Usage

#### Setup
```
npm install --save yts-api-pt
```

#### Initialize
```js
const YTS = require('yts-api-pt');

// Options are the request default options.
const yts = new YTS([{options, debug}]);
```

#### Example usage

**getMovies:**
```js
yts.getMovies({
  limit: 20,
  page: 1,
  quality: 'All',
  minimum_rating: 0,
  query_term: 'inception',
  genre: 'All',
  sort_by: 'date_added',
  order_by: 'desc',
  with_rt_ratings: true
}).then(res => console.log(res))
  .catch(err => console.error(err));

```

**getMovie:**
```js
yts.getMovie({
  movie_id: 15,
  with_images: true,
  with_cast: true
}).then(res => console.log(res))
  .catch(err => console.error(err));
```

**getSuggestions:**
```js
yts.getSuggestions(15)
  .then(res => console.log(res))
  .catch(err => console.error(err));
```

**getParentalGuides:**
```js
yts.getParentalGuides(15)
  .then(res => console.log(res))
  .catch(err => console.error(err));
```

## Output

**getMovies:**
```js
{
  "status": "ok",
  "status_message": "Query was successful",
  "data": {
    "movie_count": 1,
    "limit": 20,
    "page_number": 1,
    "movies": [<movies>]
  },
  "@meta": {
    "server_time": 1487195100,
    "server_timezone": "EST5EDT",
    "api_version": 2,
    "execution_time": "0 ms"
  }
}
```

**getMovie:**
```js
{
  "status": "ok",
  "status_message": "Query was successful",
  "data": {
    "movie": <movie>
  },
  "@meta": {
    "server_time": 1487195033,
    "server_timezone": "EST5EDT",
    "api_version": 2,
    "execution_time": "0.01 ms"
  }
}
```

**getSuggestions:**
```js
{
  "status": "ok",
  "status_message": "Query was successful",
  "data": {
    "movie_count": 4,
    "movies": [<movies>]
  },
  "@meta": {
    "server_time": 1487194963,
    "server_timezone": "EST5EDT",
    "api_version": 2,
    "execution_time": "0 ms"
  }
}
```

**getParentalGuides:**
```js
{
  "status": "ok",
  "status_message": "Query was successful",
  "data": {
    "parental_guide_count": 1,
    "parental_guides": [{
      "type": "Info",
      "parental_guide_text": "Parental Guide for all the movies will be republished soon. Thank you for understanding!"
    }]
  },
  "@meta": {
    "server_time": 1487194752,
    "server_timezone": "EST5EDT",
    "api_version": 2,
    "execution_time": "0 ms"
  }
}
```

**Movie Example:**
```js
{
  "id": 1606,
  "url": "https://yts.ag/movie/inception-2010",
  "imdb_code": "tt1375666",
  "title": "Inception",
  "title_english": "Inception",
  "title_long": "Inception (2010)",
  "slug": "inception-2010",
  "year": 2010,
  "rating": 8.8,
  "runtime": 148,
  "genres": [
    "Action",
    "Adventure",
    "Crime",
    "Mystery",
    "Sci-Fi",
    "Thriller"
  ],
  "summary": "",
  "description_full": "",
  "synopsis": "",
  "yt_trailer_code": "YoHD9XEInc0",
  "language": "English",
  "mpa_rating": "PG-13",
  "background_image": "https://yts.ag/assets/images/movies/Inception_2010/background.jpg",
  "background_image_original": "https://yts.ag/assets/images/movies/Inception_2010/background.jpg",
  "small_cover_image": "https://yts.ag/assets/images/movies/Inception_2010/small-cover.jpg",
  "medium_cover_image": "https://yts.ag/assets/images/movies/Inception_2010/medium-cover.jpg",
  "large_cover_image": "https://yts.ag/assets/images/movies/Inception_2010/large-cover.jpg",
  "state": "ok",
  "torrents": [{
    "url": "",
    "hash": "",
    "quality": "720p",
    "seeds": 634,
    "peers": 108,
    "size": "1.07 GB",
    "size_bytes": 1148903752,
    "date_uploaded": "2015-11-01 00:14:37",
    "date_uploaded_unix": 1446351277
  }],
  "date_uploaded": "2015-11-01 00:14:37",
  "date_uploaded_unix": 1446351277
}
```

# License

MIT License

Copyright (c) 2017 - yts-api-pt - Released under the MIT license.

Permission is hereby granted, free of charge, to any person obtaining a copy
of this software and associated documentation files (the "Software"), to deal
in the Software without restriction, including without limitation the rights
to use, copy, modify, merge, publish, distribute, sublicense, and/or sell
copies of the Software, and to permit persons to whom the Software is
furnished to do so, subject to the following conditions:

The above copyright notice and this permission notice shall be included in all
copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR
IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY,
FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE
AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER
LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM,
OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE
SOFTWARE.
