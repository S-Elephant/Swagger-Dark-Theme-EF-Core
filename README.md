# How to use a Swagger Dark Theme in EF Core .NET 10

Here's how to implement a dark theme for Swagger UI in your .NET 10 project.

In your backend project:

1. Add the following css file `wwwroot/swagger-ui/dark-theme.css`. An example dark theme CSS file can be taken from [here](https://raw.githubusercontent.com/Amoenus/SwaggerDark/refs/heads/master/SwaggerDark.css) (currently has a MIT license).

2. In `program.cs`:
   ```c#
   if (app.Environment.IsDevelopment()) // As a security best practice, you should only enable this code in development.
   {
   	app.UseStaticFiles(); // Required for serving custom CSS files. Security note: placing this before authentication middleware means that the static files aren't protected! If you need this line for production code as well then place this line outside of this if-statement.
   	app.UseSwagger();
   	app.UseSwaggerUI(options =>
   	{
   		options.InjectStylesheet("/swagger-ui/dark-theme.css");
   	});
   }
   ```
3. Run your backend project, open the swagger page in your browser and hard refresh your browser (usually **[CTRL] + [F5]**) while on that page.

That's it. No more NuGets or other nonsense required. Well.. Except for the custom CSS file. No more flash bangs in your face or lighting up your entire village whenever you want to test an endpoint.