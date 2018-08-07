# Hello

A cononical Hello World Application bootstrapped with Elixir/Phoenix, along with notes from a tour of the generated code.

## First Feature

First Feature will print a string when a specific URL is loaded.
To start your Phoenix app:

Steps to create:

1.  edit `router.ex` to point a URL to code
2.  add a controller to `web/controllers`
3.  add a view to `web/views`
4.  add a template to `web/template`

### Dynamic Data

Hello World is great, but we can dynamically greet users based on the name passed to the URL.

1.  edit the `hello_controller.ex` to pattern match a `:name`

    ```elixir
    def world(conn, %{"name" => name}) do
        render conn, "world.html", name: name
      end
    ```

2.  make use of the name in the template `web/templates/hello/world.html`

## Phoenix File Structure

Out of the box, as soon as you run `mix phoenix.new app_name`, you get the following file structure:

- `config`for configuration.
  - there is a master `config.exs` file, plus one for each environment `dev.exs` `prod.exs` `test.exs` and `prod.secret.exs`
  - switch between prod, dev, and test via the `MIX_ENV` variable
- `lib` for ong running propcesses
- `test` for tests
- `web` for models, views, and controllers

Fun fact, when in dev mode, the files in `lib` do not get reloaded using _live reload_.

### The Router

The router is the last plug in the endpoint. It establishes a connection, calls a pipeline, or set of functions, based on the environment( browser or api ) and then calls a specified controller.

For the example code:

```elixir
scope "/", Hello do
    pipe_through :browser # Use the default browser stack

    get "/hello/:name", HelloController, :world
    get "/", PageController, :index
  end
```

the `/hello/:name` route calls the `HelloController`
and the `/` route calls the `PageController`

### The V and the C

In Phoenix, most of the HTML and JS will go in the web directory.

- The `models` `views` and `controllers` directories are present, as is to be expected. However, there are also `templates` and `static` directories. Phoenix seperates the `templates` from the `views`. `static` exists for distinguishing static content.

That's it, a basic tour of the Phoenix Framework through the conocial Hello World application. While it's true, a lot of the "meat" is in the web directory, it may be a good idea to take a look at the code that runs each request:

```elixir
connection                             # Plug.Conn
  |> endpoint                          # lib/hello/endpoint.ex
  |> browser                           # web/router.ex
  |> HelloController.world             # web/controllers/hello_controller.ex
  |> HelloView.render("world.html")    # web/templates/hello/world.html.eex
```

---

- Install dependencies with `mix deps.get`
- Create and migrate your database with `mix ecto.create && mix ecto.migrate`
- Install Node.js dependencies with `npm install`
- Start Phoenix endpoint with `mix phoenix.server`

Now you can visit [`localhost:4000`](http://localhost:4000) from your browser.

Ready to run in production? Please [check our deployment guides](http://www.phoenixframework.org/docs/deployment).

## Learn more

- Official website: http://www.phoenixframework.org/
- Guides: http://phoenixframework.org/docs/overview
- Docs: https://hexdocs.pm/phoenix
- Mailing list: http://groups.google.com/group/phoenix-talk
- Source: https://github.com/phoenixframework/phoenix
