# Express JS
 - [Express](https://expressjs.com/) is a fast, unopinionated, minimalist web framework for Node JS.
 - It's a 'server-side' or 'backend' framework similar to: [ASP.NET Core](https://dotnet.microsoft.com/en-us/apps/aspnet) (C#), [Django](https://www.djangoproject.com/) (Python), [Ktor](https://ktor.io/) (Kotlin), or [Spring Boot](https://spring.io/projects/spring-boot) (Java).
 - Like many frameworks, Express makes build rest API's/Microservices with Node JS much easier.
```bash
npm i express
```

## Server
```ts
import express, { Application, Request, Response } from 'express';

const app: Application = express()

app.get('/api', (req :Request, res :Response) => {
  res.send('something to a client')
})

const port: number = 5000
app.listen(port, () => console.log(`listen for request at ${port}`))
```

## Routes
 - **Routing** refers to how an application’s endpoints (URIs) respond to client requests. For an introduction to routing, see Basic routing.
```ts
import { Router } from 'express';
import { getTodos } from '../controllers/getTodos'

const router: Router = Router()

router.get('/', getTodos)
```

## Controllers
```ts
import { RequestHandler } from 'express';

const getTodos: RequestHandler = (req, res) => {
  res.json(todos)
}
```

## Middleware
```ts
import { log } from "console";
import { NextFunction, Request, Response } from "express";
import moment from "moment";

export const logger = (req: Request, res: Response, next: NextFunction) => {
    log(`${req.protocol}://${req.get('host')}${req.originalUrl}: ${moment().format()}`)
    next()
}
```