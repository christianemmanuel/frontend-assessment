## Vue + Vite

Frontend Assessment | Christian Emmanuel Concepcion

## Technologies used

Vuejs, SCSS, Taildwind CSS

## Setup

### `npm install`

Install node_modules

### `npm run dev`

Runs the app in the development mode.

## Exercise 1

For this project, I used Vue.js, Tailwind CSS, and SCSS. The project is divided into two components: the **Banner** component and the **CardList** component. To keep the code clean and organized, the data is stored in JSON format in the public folder. For CSS naming conventions, I’m using the BEM methodology.

Preview: https://exercise-1-alpha.vercel.app/

## Exercise 2

On desktop view, I created a tabbed menu, and for small screens or mobile view, I implemented an accordion. This was achieved using media queries. I’m using Vue.js, and the onMounted hook runs when the component is mounted. It fetches data from /data.json and updates the tabs with the fetched data.

Preview: https://exercise-2-delta.vercel.app/

Banana Explained:
1. 'b' + 'a' results in 'ba'.
2. Adding 'a' converts 'a' to NaN (Not-a-Number).
3. Concatenating 'ba' and NaN gives 'baNaN'.
4. Adding 'a' results in 'baNaNa'.
5. .toLowerCase() to ensure that a string is in lowercase, converts 'baNaNa' to 'banana'.
