# Circular structure in "getInitialProps" result

#### Why This Error Occurred

`getInitialProps` is serialized to JSON using `JSON.stringify` and sent to the client side for hydrating the page.

However, the result returned from `getInitialProps` can't be serialized when it has a circular structure.

#### Possible Ways to Fix It

Circular structures are not supported, so the way to fix this error is removing the circular structure from the object that is returned from `getInitialProps`.

##### The `req` object in `getServerSideProps`

Don't pass the whole `req` object down as props. For example, to get incoming HTTP headers, return `req.headers` instead of `req`.

```
return (
  props: {
    headers: req.headers
  }
}
```

Available data is detailed in the docs for [getServerSideProps](https://nextjs.org/docs/api-reference/data-fetching/get-server-side-props#context-parameter)
