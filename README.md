# Movies List

> Here is the [working version](https://mate-academy.github.io/vue_movies-list-edit-form/)

Implement ability to add new and edit existing movies using the MovieForm component.

1. Extract the list implemented in the [Movie List Selector](https://github.com/mate-academy/vue_movies-list-selector/) task to the `MovieList` component.
1. Show movies from `src/data/movies.json` by default.
1. Extract the form implemented in the [Movie List Add Form](https://mate-academy.github.io/vue_movies-list-edit-form/) task to the `MovieForm` component.
1. By default `MovieForm` allows to add a Movie.
1. If you select a movie in the list, the form should allow to edit its data.
   - Prefill the form with current movie data:
      ```js
      watch(
        () => props.movie?.imdbId,
        () => { ... },
      );
      ```
   - Rename the submit button to `Update`
   - Add the `Cancel` button that clears the form and cancels the selection.
   - On submit update the movie in the list.
1. Focus the `movie-form__title` in [onMounted](https://vuejs.org/guide/essentials/lifecycle.html#registering-lifecycle-hooks), when a movie is selected or form is cleared.
1. Add a `x` button with `data-cy="movie__delete-button"` to each card to delete it from the list.
    ```html
    <div class="card" data-cy="movie">
      <header class="card-header is-justify-content-space-between">
        ...

        <button
          class="card-header-icon"
          data-cy="movie__delete-button"
        >
          <span class="icon">
            <i class="fas fa-xmark"></i>
          </span>
        </button>
      </header>

      ...
    </div>
    ```
1. Add and delete movies smoothly (for example add `opacity: 0` and `translateY(-20px)`).

## Instructions

- Install Prettier Extention and use this [VSCode settings](https://mate-academy.github.io/fe-program/tools/vscode/settings.json) to enable format on save.
- Open one more terminal and run tests with `npm test` to ensure your solution is correct.
- Replace `<your_account>` with your Github username in the [DEMO LINK](https://<your_account>.github.io/vue_movies-list-edit-form/) and add it to the PR description.
