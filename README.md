# HTML5
HTML 5 documentation

What is initial scale, user-scalable, minimum-scale, maximum-scale attribute in meta tag?

I was going through the source code of a website and found this piece of code.

<meta name="viewport" content="width=device-width, initial-scale=1.0, user-scalable=1.0, minimum-scale=1.0, maximum-scale=1.0">

They are viewport meta tags, and is most applicable on mobile browsers.

width=device-width

This means, we are telling to the browser “my website adapts to your device width”.

initial-scale

This defines the scale of the website, This parameter sets the initial zoom level, which means 1 CSS pixel is equal to 1 viewport pixel. This parameter help when you're changing orientation, or preventing default zooming. Without this parameter, responsive site won't work.

maximum-scale
Maximum-scale defines the maximum zoom. When you access the website, top priority is maximum-scale=1, and it won’t allow the user to zoom.

minimum-scale
Minimum-scale defines the minimum zoom. This works the same as above, but it defines the minimum scale. This is useful, when maximum-scale is large, and you want to set minimum-scale.

user-scalable
User-scalable assigned to 1.0 means the website is allowing the user to zoom in or zoom out.

But if you assign it to user-scalable=no, it means the website is not allowing the user to zoom in or zoom out.

user-scalable:

user-scalable=yes (default) to allow the user to zoom in or zoom out on the web page;

user-scalable=no to prevent the user from zooming in or zooming out.

you can get more detail infomation by reading the following articles, hope it helpful for you!

https://i.stack.imgur.com/bAzG0.png

# Javascript Interfaces:

Though JavaScript does not have the interface type, it is often times needed. For reasons relating to JavaScript's dynamic nature and use of Prototypical-Inheritance, it is difficult to ensure consistent interfaces across classes -- however, it is possible to do so; and frequently emulated.

At this point, there are handfuls of particular ways to emulate Interfaces in JavaScript; variance on approaches usually satisfies some needs, while others are left unaddressed. Often times, the most robust approach is overly cumbersome and stymies the implementor (developer).

Here is an approach to Interfaces / Abstract Classes that is not very cumbersome, is explicative, keeps implementations inside of Abstractions to a minimum, and leaves enough room for dynamic or custom methodologies:

function resolvePrecept(interfaceName) {
    var interfaceName = interfaceName;
    return function curry(value) {
        /*      throw new Error(interfaceName + ' requires an implementation for ...');     */
        console.warn('%s requires an implementation for ...', interfaceName);
        return value;
    };
}
var iAbstractClass = function AbstractClass() {
    var defaultTo = resolvePrecept('iAbstractClass');

    this.datum1 = this.datum1 || defaultTo(new Number());
    this.datum2 = this.datum2 || defaultTo(new String());

    this.method1 = this.method1 || defaultTo(new Function('return new Boolean();'));
    this.method2 = this.method2 || defaultTo(new Function('return new Object();'));

};
var ConcreteImplementation = function ConcreteImplementation() {

    this.datum1 = 1;
    this.datum2 = 'str';

    this.method1 = function method1() {
        return true;
    };
    this.method2 = function method2() {
        return {};
    };

    //Applies Interface (Implement iAbstractClass Interface)
    iAbstractClass.apply(this);  // .call / .apply after precept definitions
};

# Drawbacks

Though this helps implement consistency throughout your software to a significant degree, it does not implement true interfaces -- but emulates them. Though definitions, defaults, and warnings or errors are explicated, the explication of use is enforced & asserted by the developer (as with much of JavaScript development).

This is seemingly the best approach to "Interfaces in JavaScript", however, I would love to see the following resolved:

- Assertions of return types
- Assertions of signatures
- Freeze objects from delete actions
- Assertions of anything else prevalent or needed in the specificity of the JavaScript community
