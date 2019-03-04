<p align="center">
    <img src="https://raw.githubusercontent.com/nialloc9/roman_numerals/master/screenshots/convert16.png" alt='coverting 16 to roman numerals' width="400">
</p>

# roman_numerals

An API and a web based application that converts numbers to roman numerals.

### Prerequisites

- install npm and node: <a href="https://docs.npmjs.com/downloading-and-installing-node-js-and-npm">https://docs.npmjs.com/downloading-and-installing-node-js-and-npm</a>

- install bunyan and nodemon

        $ npm i -g bunyan nodemon

### Usage

- cd into project root directory

        $ cd ./server && npm install && npm start

- open new terminal window.

- cd into project root directory

        $ cd ./client && npm install && npm start

- Screenshots of project are available in the screenshot folder

### Testing

- cd into project root directory

        $ cd ./server && npm test

# Original Technical Task

Create an API and a web based application that converts numbers to roman numerals.

### Technologies to use

- Node.js 8.x

- React

### Minimum Criteria

- Converts numbers 1 to 3999 to the equivalent value in roman numerals.

- Converts Roman Numerals "I" to “MMMCMXCIX” to the equivalent numeric value. In reverse

- Simple react based web interface that uses an API created by you.

- Readme file explaining how to run the application, explain your approach and list any improvements you would make.

### Ideally

- Use ES6 syntax.

### You can

- Use any NPM modules in your application except for the conversion of numbers and roman numerals.

- Be as creative as you like on the user interface, use any client libraries you want.

- Don't worry too much about optimising the client code (unless you want to), you can explain how you would do this in the Readme.

### More information

- Roman numerals: <a href="https://en.wikipedia.org/wiki/Roman_numerals">https://en.wikipedia.org/wiki/Roman_numerals</a>

# Approach

Below you will find a combination of assumptions made, notes, intended client approach, and intended server approach.

### Assumptions

- The endpoints doe not need to be authenticated. (If they do a bearer token will be added to the headers and a 401 status code will be returned if token is invalid)

- The minimum criteria seems to be missing part of it's description. "In reverse ". I will ignore this until I get confirmation of what it is.

- Data transfer will be accomplished using a Rest API. (For example not via sockets or using other technologies such as graphQL)

- All numbers will be integers and not floats or any other data type.

- The data will not be stored on either the client or the server after request has been made.

- At any time only one integer or roman numeral will be passed in a request to the api.

- No specifications on browser support have been made so I will make the assumption to support the latest 2 versions of each browser.

- Initial value does not need to be passed back in response.

- API will only be consumed by this client.

- Supported devices not in specification. Going to assume a mobile first approach.

### Notes

- Create react app is used as a boilerplate to get going as fast as possible. It will handle pollyfills using browserlist and babel-env. If needed I would create a webpack config to build the client with hot reloading, code splitting, pollyfills etc.

- Examples of some webpack configs done in other projects: <a href="https://github.com/nialloc9/currying">https://github.com/nialloc9/currying</a> and <a href="https://github.com/nialloc9/reactReduxJestBoilerplate">https://github.com/nialloc9/reactReduxJestBoilerplate</a>

### Intended approach Client

- As the project will only have one view I will use local state and pass that down instead of using a data store such as redux. This would be overkill for something like this. I will split the logic and view into 2. A container and a view. While inheritance could be used here I will use object composition instead as react favors it.

- Validation will be custom and created to be used individually or together using a pipeline. The pipeline will call each validator in turn with the result of the previous. If the final result is a string display this message. This allows the validators to be be used in any order while keeping the code clean, neat, and reuseable.

### Intended approach Server

- I will add middleware to prevent cors and other security issues.

- I will add middleware to log all incoming requests.

- A model will be used for validating the incoming data.

- The transformer functions for manipulating the data will be abstracted into a utility file to keep code clean and make it easier to test.

- I will use enveloping to ensure all responses from the server follow the same data structure. { timestamp, data }. This allows such things a requestId and other data to be added to the object later without effecting the core data struture returned.

### Intended API endpoits

- GET /manipulate/roman-numeral/:value
- GET /manipulate/number/:value

### Improvements

- Testing can be increased to 100% coverage for both client and server.
- End to end testing can be integrated to test application from the viewpoint of the user.
- Recent conversions could be saved in local state and shown on the left as quick references. (This is outside the scope of this project but would be a nice future feature)
