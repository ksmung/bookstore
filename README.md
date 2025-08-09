# bookstore


Install the reusable service project as npm dependency:
```
npm install $(npm pack ../products-service -s)
```

Install all other packages and simplify the overall dependency structure
```
npm install && npm dedupe
```