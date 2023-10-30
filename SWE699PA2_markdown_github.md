# SWE 699 PA 2
## Team: Neural Nexus
##### Anish Kumar Saranga           G01376251
##### Ayaan Ehsaan Mohammad         G01355098
##### Murali Sai Lakith Pusarla     G01381718
-------------
### Steps before executing code:


- Run pip install z3-solver
- Run python se.py using command 'python se.py' or 'python3 se.py'(this will execute test1() and test2())

 ### Answers to the given questions:
1. Briefly describe what you did for part 1 and part 2.

    a. Part 1:
    
        - The algorithm accepts an encoded DNN and an 'inputs' argument which by default takes two real Z3 variables as input nodes. This can be generalized by calling the function by passing the specific number of input neurons to the 'inputs' parameter.
        - The functions 'create_random_nn()' and 'get_hidden_and_output_nodes()' help create a dnn with random weights and bias values (both within the range [-5, 5]).
        - The my_symbolic_execution function symbolically executes a Deep Neural Network (DNN) using the Z3 package in Python. It calculates the symbolic expressions representing the DNN's behavior, including ReLU activation, and records them as constraints. The function then measures the runtime of this symbolic execution and outputs the results. The function acts as a powerful tool for analyzing and verifying DNN behavior without performing actual computations.
        - The symbolic_states variable keeps track of outputs of all the neurons. Each layer is tracked using the layer_states variable and then finally returns the 'z3.And'ed version of all items of symbolic_states.
    b. Part 2:
    
        - We defined a function named my_interval_execution that serves the purpose of estimating the potential output ranges for individual nodes within a deep neural network (DNN). The process involves iterating through each layer of the DNN, considering the weights, biases, and activation functions applied to each node. 
        - Input ranges for these nodes are assumed to be stored in the pre dictionary. 
        - For each layer, the code calculates the potential output range for every node by multiplying the input ranges with their corresponding weights, summing the results, adding the node's bias, and, if the activation function is ReLU, applying the rectified linear unit activation. The code then assigns a variable name to each node based on its position within the network, such as "n01" for the first node in the second layer. 
        - The calculated node ranges are stored in the all_node_ranges dictionary, which is updated with each layer's results. Once all layers are processed, the function returns all_node_ranges, which contains the input and output range information for all nodes in the neural network. 
        - We essentially implemented a range propagation algorithm, allowing us to analyze the potential output ranges of individual nodes in a neural network, which can be valuable for understanding the network's behavior and uncertainty.
2. Describe the plots and conclusions you have for scalability of both parts 1 and 2

    a. Part 1:
        ![Test image](https://github.com/lakith-pusarla/PA2/blob/main/comparision_plot.png) 
    b. Part 2



Markdown is a lightweight markup language based on the formatting conventions
that people naturally use in email.
As [John Gruber] writes on the [Markdown site][df1]

> The overriding design goal for Markdown's
> formatting syntax is to make it as readable
> as possible. The idea is that a
> Markdown-formatted document should be
> publishable as-is, as plain text, without
> looking like it's been marked up with tags
> or formatting instructions.

This text you see here is *actually- written in Markdown! To get a feel
for Markdown's syntax, type some text into the left window and
watch the results in the right.

## Tech

Dillinger uses a number of open source projects to work properly:

- [AngularJS] - HTML enhanced for web apps!
- [Ace Editor] - awesome web-based text editor
- [markdown-it] - Markdown parser done right. Fast and easy to extend.
- [Twitter Bootstrap] - great UI boilerplate for modern web apps
- [node.js] - evented I/O for the backend
- [Express] - fast node.js network app framework [@tjholowaychuk]
- [Gulp] - the streaming build system
- [Breakdance](https://breakdance.github.io/breakdance/) - HTML
to Markdown converter
- [jQuery] - duh

And of course Dillinger itself is open source with a [public repository][dill]
 on GitHub.

## Installation

Dillinger requires [Node.js](https://nodejs.org/) v10+ to run.

Install the dependencies and devDependencies and start the server.

```sh
cd dillinger
npm i
node app
```

For production environments...

```sh
npm install --production
NODE_ENV=production node app
```

## Plugins

Dillinger is currently extended with the following plugins.
Instructions on how to use them in your own application are linked below.

| Plugin | README |
| ------ | ------ |
| Dropbox | [plugins/dropbox/README.md][PlDb] |
| GitHub | [plugins/github/README.md][PlGh] |
| Google Drive | [plugins/googledrive/README.md][PlGd] |
| OneDrive | [plugins/onedrive/README.md][PlOd] |
| Medium | [plugins/medium/README.md][PlMe] |
| Google Analytics | [plugins/googleanalytics/README.md][PlGa] |

## Development

Want to contribute? Great!

Dillinger uses Gulp + Webpack for fast developing.
Make a change in your file and instantaneously see your updates!

Open your favorite Terminal and run these commands.

First Tab:

```sh
node app
```

Second Tab:

```sh
gulp watch
```

(optional) Third:

```sh
karma test
```

#### Building for source

For production release:

```sh
gulp build --prod
```

Generating pre-built zip archives for distribution:

```sh
gulp build dist --prod
```

## Docker

Dillinger is very easy to install and deploy in a Docker container.

By default, the Docker will expose port 8080, so change this within the
Dockerfile if necessary. When ready, simply use the Dockerfile to
build the image.

```sh
cd dillinger
docker build -t <youruser>/dillinger:${package.json.version} .
```

This will create the dillinger image and pull in the necessary dependencies.
Be sure to swap out `${package.json.version}` with the actual
version of Dillinger.

Once done, run the Docker image and map the port to whatever you wish on
your host. In this example, we simply map port 8000 of the host to
port 8080 of the Docker (or whatever port was exposed in the Dockerfile):

```sh
docker run -d -p 8000:8080 --restart=always --cap-add=SYS_ADMIN --name=dillinger <youruser>/dillinger:${package.json.version}
```

> Note: `--capt-add=SYS-ADMIN` is required for PDF rendering.

Verify the deployment by navigating to your server address in
your preferred browser.

```sh
127.0.0.1:8000
```

## License

MIT

**Free Software, Hell Yeah!**

[//]: # (These are reference links used in the body of this note and get stripped out when the markdown processor does its job. There is no need to format nicely because it shouldn't be seen. Thanks SO - http://stackoverflow.com/questions/4823468/store-comments-in-markdown-syntax)

   [dill]: <https://github.com/joemccann/dillinger>
   [git-repo-url]: <https://github.com/joemccann/dillinger.git>
   [john gruber]: <http://daringfireball.net>
   [df1]: <http://daringfireball.net/projects/markdown/>
   [markdown-it]: <https://github.com/markdown-it/markdown-it>
   [Ace Editor]: <http://ace.ajax.org>
   [node.js]: <http://nodejs.org>
   [Twitter Bootstrap]: <http://twitter.github.com/bootstrap/>
   [jQuery]: <http://jquery.com>
   [@tjholowaychuk]: <http://twitter.com/tjholowaychuk>
   [express]: <http://expressjs.com>
   [AngularJS]: <http://angularjs.org>
   [Gulp]: <http://gulpjs.com>

   [PlDb]: <https://github.com/joemccann/dillinger/tree/master/plugins/dropbox/README.md>
   [PlGh]: <https://github.com/joemccann/dillinger/tree/master/plugins/github/README.md>
   [PlGd]: <https://github.com/joemccann/dillinger/tree/master/plugins/googledrive/README.md>
   [PlOd]: <https://github.com/joemccann/dillinger/tree/master/plugins/onedrive/README.md>
   [PlMe]: <https://github.com/joemccann/dillinger/tree/master/plugins/medium/README.md>
   [PlGa]: <https://github.com/RahulHP/dillinger/blob/master/plugins/googleanalytics/README.md>
