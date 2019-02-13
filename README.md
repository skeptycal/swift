<p align="center">
  <img src="images/logo.png">
</p>

# Swift for TensorFlow

> S4TF: No barriers.

Swift for TensorFlow (aka S4TF) is a next-generation machine learning framework,
incorporating the latest research across: machine learning, compilers, 
differential programming, systems design, and beyond. This project is
approaching version _0.2_; it is neither feature complete nor production-ready.
But it is ready for _pioneers_ to try it for your own projects, give us
feedback, and help shape the future!

The S4TF project is currently focusing on 2 kinds of users:

 1. **Advanced ML Researchers** who are limited by current ML frameworks.
    S4TF's advantages include a seamless integration with a modern general-purpose
    language, allowing for more dynamic and sophisticated models. Fast
    abstractions can be developed "in user-space" (as opposed to in C/C++
    aka "framework-space"), resulting in modular APIs that can be easily
    customized.

 2. **ML Learners** who are just getting started with machine learning. Thanks
    to Swift's support for quality tooling (e.g. context-aware autocomplete),
    S4ML can be one of the most productive ways to get started learning the
    fundamentals of machine learning.

## Getting started

 - **Colab**: The fastest way to get started is to try out S4TF right in your
   browser. Just open up our [getting started
   notebook](https://colab.research.google.com/github/tensorflow/swift-tutorials/blob/master/iris/swift_tensorflow_tutorial.ipynb) (or start from a
   [blank notebook](https://colab.research.google.com/github/tensorflow/swift/blob/master/notebooks/blank_swift.ipynb))!
   Read more in our [usage guide](Usage.md).

 - **Install locally**: you can [download a pre-built Swift for TensorFlow
   package](Installation.md). After installation, you can follow these
   [step-by-step instructions](Usage.md) to build and execute a S4TF program
   on your computer.

 - **Compile from source**: If you'd like to customize S4TF or even contribute
   back, follow our [instructions on building the S4TF compiler from source,
   from in the compiler's README](https://github.com/apple/swift/tree/tensorflow).

Please do join the
[swift@tensorflow.org mailing list](https://groups.google.com/a/tensorflow.org/d/forum/swift)
to hear the latest announcements, get help, and share your thoughts!

## Why S4TF?

Swift for TensorFlow is a new way to develop machine learning models. It
gives you the power of
[TensorFlow](https://www.tensorflow.org) directly integrated into the
[Swift programming language](https://swift.org/about). We believe that
machine learning paradigms are so important that they deserve
**first-class language and compiler support**. 

Optimizing parameters by taking the gradient of functions is a fundamental
primitive of machine learning. With Swift for TensorFlow,
you can write a normal function using arbitrary data types, and then
take the derivative of it with just a single annotation.

```swift
import TensorFlow

var x = Tensor<Float>([[1, 2], [3, 4]])

@differentiable
func myWackyPowPlus(ofBase base: Tensor<Float>,
                    toExponent exponent: Int) -> Tensor<Float>
  var x = base
  for _ in 1...exponent {
      x += x • base // alternatively: x += matmul(x, base)
      print(x)  // Debugging!
  }
  return x
}
```

Beyond derivatives, the S4TF project comes with a sophisticated toolchain
to make users more productive. You can run Swift interactively in a Jupyter
notebook, and get helpful autocomplete suggestions to help you explore the
massive API surface of a modern deep learning library. You can [get started
right in your browser in
seconds](https://colab.research.google.com/github/tensorflow/swift-tutorials/blob/master/iris/swift_tensorflow_tutorial.ipynb)!

Migrating to S4TF is really easy thanks to Swift's powerful Python integration.
You can incrementally migrate your Python code over (or continue to use your
favorite Python libraries), because you can easily call your favorite Python
library with a familiar syntax:

```swift
import Python
import TensorFlow

let np = Python.import("numpy")

let myNumpyArray = np.arange([10, 10])  // Create a 10x10 numpy array.
let myTensor = Tensor(fromNumpyArray: myNumpyArray)  // Seamless integration!
```

## Documentation

### Getting started

- [Swift for TensorFlow Design Overview](docs/DesignOverview.md)
- [Why *Swift* for TensorFlow?](docs/WhySwiftForTensorFlow.md)
- [Sample Models](https://github.com/tensorflow/swift-models)
- [Tutorials](https://github.com/tensorflow/swift-tutorials)]
- [Frequently Asked Questions](FAQ.md)
- [Swift Tensor API Reference](https://www.tensorflow.org/api_docs/swift/Structs/Tensor)

### Technology deep dive

The Swift for TensorFlow project builds on top of powerful theoretical
foundations. For insight into some of the underlying technologies, check
out the following documentation.

> Beware: the project is moving very quickly, and thus some of these documents
> are slightly out of date as compared to the current state-of-the-art.

- [Automatic Differentiation Whitepaper](docs/AutomaticDifferentiation.md)
- [Automatic Differentiation Manifesto](https://gist.github.com/rxwei/30ba75ce092ab3b0dce4bde1fc2c9f1d)
- [Python Interoperability](docs/PythonInteroperability.md)
- [Aggregate Parameters and Parameter Update](docs/AggregateParameters.md)
- [Graph Program Extraction](docs/GraphProgramExtraction.md)

## Source code

Compiler and standard library development of Swift for TensorFlow happens
on the `tensorflow` branch of the
[apple/swift](https://github.com/apple/swift/tree/tensorflow) repository.

Additional code repositories that make up the core of project include:

 - [Debugger and REPL support](http://github.com/apple/swift-lldb/tree/tensorflow)
 - [High level APIs](https://github.com/tensorflow/swift-apis)

> Swift for TensorFlow is **not** intended to remain a long-term fork of the official 
> Swift language. New language features will eventually go through the Swift evolution process
> as part of being considered for being pulled into master.

### Jupyter Notebook support

[Jupyter Notebook](http://jupyter.org/) support for Swift is under development at
[google/swift-jupyter](https://github.com/google/swift-jupyter).

## Community

Swift for TensorFlow discussions happen on the
[swift@tensorflow.org mailing list](https://groups.google.com/a/tensorflow.org/d/forum/swift).

For the most part, the core team's development is tracked in
[JIRA].

### Bugs Reports and Feature Requests

Before reporting an issue, please check the [Frequently Asked Questions](FAQ.md)
to see if your question has already been addressed.

For questions about general use or feature requests, please send an email to
the [mailing list](mailto:swift@tensorflow.org) or search for relevant issues
in the [JIRA issue tracker](https://bugs.swift.org/projects/TF/issues/?filter=allopenissues).

For the most part, the core team's development is also tracked in
[JIRA](https://bugs.swift.org/secure/RapidBoard.jspa?rapidView=17&projectKey=TF&view=planning).

### Contributing

We welcome source code contributions: please read 
[Contributing Code](https://swift.org/contributing/#contributing-code).
It is always a good idea to discuss your plans on the mailing list before
making any major submissions.

Check out our [starter bugs](https://bugs.swift.org/issues/?filter=11323) if
you'd like to get involved but don't know where to start!

### Code of Conduct

In the interest of fostering an open and welcoming environment, we as
contributors and maintainers pledge to making participation in our project and
our community a harassment-free experience for everyone, regardless of age, body
size, disability, ethnicity, gender identity and expression, level of
experience, education, socio-economic status, nationality, personal appearance,
race, religion, or sexual identity and orientation.

The Swift for TensorFlow community is guided by our [Code of
Conduct](CODE_OF_CONDUCT.md), which we encourage everybody to read before
participating.
