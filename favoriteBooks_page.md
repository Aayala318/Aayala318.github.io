## Favorite Books

**Description:** This project was mainly focused on creating and experimenting with the navbar. This was one of my early attempts in creating a navber, it does not have much functionality but does have a logout button within it. The project allows users to add book titles along with the author, they can also favorite and unfavorite books. When a user adds a book, that book will automatically be added to their favorited list and be displayed on their main page. Books that are not favorited by the current user with be in a "Other Books" list.

### 1. My code for creating and styling the navbar.

```html
    <nav class="navbar navbar-expand-lg navbar-dark bg-dark">
        <div class="container">
            <a class="navbar-brand" href="#">Favorite Books</a>
            <button class="navbar-toggler" type="button" data-toggle="collapse" data-target="#navbarText"
                aria-controls="navbarText" aria-expanded="false" aria-label="Toggle navigation">
                <span class="navbar-toggler-icon"></span>
            </button>
            <div class="collapse navbar-collapse" id="navbarText">
                <ul class="navbar-nav mr-auto"></ul>
                <span class="navbar-text">
                    Welcome, {{request.session.greeting}} </a> <a href="/logout" role="button"
                        class="btn btn-sm btn-info ml-2 text-white">Logout</a>
                </span>
            </div>
        </div>
    </nav>
``` 

For more details see [GitHub Flavored Markdown](https://guides.github.com/features/mastering-markdown/).
