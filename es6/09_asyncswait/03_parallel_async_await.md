---
layout: default
title: Parallel Async Await
nav_order: 2
parent: Async/Await
grand_parent: ES6
---

## Parallel Async Await

```js
const getMoviesParallel = async () => {
  try {
    const [moviesResponse, detailResponse] = await Promise.all([
      fetch("https://yts.mx/api/v2/list_movies.json"),
      fetch("https://yts.mx/api/v2/movie_details.json?movie_id=10"),
    ]);
    const [movies, detail] = await Promise.all([
      moviesResponse.json(),
      detailResponse.json(),
    ]);
    console.log(movies, detail);
  } catch (error) {
    console.log(error);
  } finally {
    console.log("done");
  }
};

getMoviesParallel();
```

{: .highlight }

> Promise {&lt;pending&gt;}
>
> {status: 'ok', status_message: 'Query was successful', data: {…}, @meta: {…}}
>
> {status: 'ok', status_message: 'Query was successful', data: {…}, @meta: {…}}
>
> done

이런 코드들을 깔끔하게 만들어주기 위해 axios와 같은 라이브러리를 사용하기도 한다.
