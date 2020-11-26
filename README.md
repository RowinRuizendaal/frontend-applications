## Final product link

[WIP](https://google.com)


## First product link

[demo](https://rowinruizendaal.github.io/frontend-data/)



## Volkskrant assignment

For the Volkskrant, we are having a look into the RDW datasets that are provided to find interesting insights for a potential article about parking, where it is all about cars.

The assignment is to filter and find connections with different datasets where 'parking' (cars) is the middle word for each of these datasets, one head question can be answered by the datasets. The main goal of this assignment is to link interesting links with each other and to filter data out of the available datasets

This wiki also contains assignments apart from the volkrant, these are practice datasets that were filled in by the students that are following the course: datavizualisation.


## Concept

Making a geographical map for parking places where you can see how much you need to pay for a certain parking place and how much it cost per hour also I am going to note down how you can pay the parking fee (cash, banknotes, VISA etc)

## Research question

How can you pay at a specific parking garage (by card, coins, banknotes, visa etc.)

 - Are there more parking garages where you can pay by card in 2020?
 - Are there still parking garages where you can pay by coins/banknotes

 ## Sub questions

- Are there parking areas where you can pay with cryptocoins?
- How far apart are the payment terminals in a particular parking area?
- Are the payment machines wheelchair-proof (height of machines)?
- Where can you still pay with cash at a payment terminal?
- How are the payment methods (cash, pin) distributed throughout the city? Center more pin options than outside the center?

## Datasets needed

 * https://data.overheid.nl/dataset/11389-open-data-parkeren--betaalmethode-gebied (areaid, paymentmethod)
 * https://opendata.rdw.nl/Parkeren/Open-Data-Parkeren-GEBIED/adw6-9hsg (not sure yet if I am going to use this one)
 * https://opendata.rdw.nl/Parkeren/GEO-Parkeer-Garages/t5pc-eb34 (areaid, Location, AreaDesc)
 * https://opendata.rdw.nl/Parkeren/Open-Data-Parkeren-TARIEFDEEL/534e-5vdg (From peer-feedback)

The primary key (PK) in these datasets is : areaid, with this key I am able to find other datasets with this value to join each other

## Assumptions

- There are more parking spots where you can pay by card then with coins or banknotes
- Parking spots closer to the city centre have more payment options and are more expensive than ones further away

## What's done with invalid or empty values?

During developing I needed to combine datasets with eachother, during the combining some values were lost and I've decided the keep it that way, beacuse there was no way I was able to use this data because it didn't contained the values that I needed.



*Looking for a shareable component template? Go here --> [sveltejs/component-template](https://github.com/sveltejs/component-template)*

---

# svelte app

This is a project template for [Svelte](https://svelte.dev) apps. It lives at https://github.com/sveltejs/template.

To create a new project based on this template using [degit](https://github.com/Rich-Harris/degit):

```bash
npx degit sveltejs/template svelte-app
cd svelte-app
```

*Note that you will need to have [Node.js](https://nodejs.org) installed.*


## Get started

Install the dependencies...

```bash
cd svelte-app
npm install
```

...then start [Rollup](https://rollupjs.org):

```bash
npm run dev
```

Navigate to [localhost:5000](http://localhost:5000). You should see your app running. Edit a component file in `src`, save it, and reload the page to see your changes.

By default, the server will only respond to requests from localhost. To allow connections from other computers, edit the `sirv` commands in package.json to include the option `--host 0.0.0.0`.

If you're using [Visual Studio Code](https://code.visualstudio.com/) we recommend installing the official extension [Svelte for VS Code](https://marketplace.visualstudio.com/items?itemName=svelte.svelte-vscode). If you are using other editors you may need to install a plugin in order to get syntax highlighting and intellisense.

## Building and running in production mode

To create an optimised version of the app:

```bash
npm run build
```

You can run the newly built app with `npm run start`. This uses [sirv](https://github.com/lukeed/sirv), which is included in your package.json's `dependencies` so that the app will work when you deploy to platforms like [Heroku](https://heroku.com).


## Single-page app mode

By default, sirv will only respond to requests that match files in `public`. This is to maximise compatibility with static fileservers, allowing you to deploy your app anywhere.

If you're building a single-page app (SPA) with multiple routes, sirv needs to be able to respond to requests for *any* path. You can make it so by editing the `"start"` command in package.json:

```js
"start": "sirv public --single"
```

## Using TypeScript

This template comes with a script to set up a TypeScript development environment, you can run it immediately after cloning the template with:

```bash
node scripts/setupTypeScript.js
```

Or remove the script via:

```bash
rm scripts/setupTypeScript.js
```

## Deploying to the web

### With [Vercel](https://vercel.com)

Install `vercel` if you haven't already:

```bash
npm install -g vercel
```

Then, from within your project folder:

```bash
cd public
vercel deploy --name my-project
```

### With [surge](https://surge.sh/)

Install `surge` if you haven't already:

```bash
npm install -g surge
```

Then, from within your project folder:

```bash
npm run build
surge public my-project.surge.sh
```


### Sketches

![Sketches](https://raw.githubusercontent.com/wiki/RowinRuizendaal/functional-programming/assets/sketches.png)


### First product screenshot(s)

![first](https://raw.githubusercontent.com/wiki/RowinRuizendaal/functional-programming/assets/final.PNG)

![fist1](https://raw.githubusercontent.com/wiki/RowinRuizendaal/functional-programming/assets/final-2.png)


### Final product screenshot(s)

![final2](https://raw.githubusercontent.com/wiki/RowinRuizendaal/functional-programming/assets/fina-final.png)

### License

Authtor: [RowinRuizendaal](https://github.com/rowinruizendaal)

license: [MIT](https://github.com/RowinRuizendaal/functional-programming/blob/Master/LICENSE)


### Credits

[vuurvos1](https://github.com/vuurvos1) For the good coding talks in Discord ༼ つ ◕_◕ ༽つ and the helpfull help

[sreen020](https://github.com/sreen020/) For working together in Vizhub


### Vizhub tries

[Vizhub](https://vizhub.com/RowinRuizendaal)



### Resources

Arora, S. (2019, March 27). Understanding Higher-Order Functions in JavaScript - Bits and Pieces. Medium. 
https://blog.bitsrc.io/understanding-higher-order-functions-in-javascript-75461803bad

Elliott, E. (2019, July 2). Master the JavaScript Interview: What is Functional Programming? Medium. 
https://medium.com/javascript-scene/master-the-javascript-interview-what-is-functional-programming-7f218c68b3a0

Open Data | | Open Data. (n.d.). RDW. Retrieved October 29, 2020, from 
https://opendata.rdw.nl/
