# Hello

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
