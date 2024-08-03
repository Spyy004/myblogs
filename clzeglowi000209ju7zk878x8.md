---
title: "Proxy Magic: How to Bend JavaScript Objects to Your Will"
seoTitle: "Master JavaScript Objects with Proxies"
seoDescription: "Use JavaScript Proxies to customize object operations with practical examples and real-world applications"
datePublished: Sat Aug 03 2024 18:20:40 GMT+0000 (Coordinated Universal Time)
cuid: clzeglowi000209ju7zk878x8
slug: proxy-magic-how-to-bend-javascript-objects-to-your-will
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1722709049433/d54866ae-c898-4e05-97a0-f8f7db6861ea.png
ogImage: https://cdn.hashnode.com/res/hashnode/image/upload/v1722709099883/fe540cec-9045-4ef6-b035-916475ca5285.png
tags: tutorial, javascript, web-development, beginner, javascript-framework

---

# Unveiling the Magic of JavaScript Proxies: A Deep Dive

Hey there, JavaScript enthusiasts! Today, we're going to explore a powerful yet often overlooked feature of modern JavaScript: the Proxy object. If you've ever wished you could intercept and customize fundamental operations on JavaScript objects, then you're in for a treat. Buckle up as we dive into the world of Proxies!

## What is a Proxy?

In JavaScript, a Proxy is an object that wraps another object (called the target) and can intercept fundamental operations on that object, like getting or setting properties. It's like having a bodyguard for your object that can modify how it behaves without changing the object itself.

## The Anatomy of a Proxy

A Proxy is created with two parameters:

1. The target object
    
2. A handler object that defines the operations to intercept (called traps)
    

Here's the basic syntax:

```javascript
const proxy = new Proxy(target, handler);
```

## Your First Proxy: Logging Property Access

Let's start with a simple example. We'll create a Proxy that logs every time a property is accessed:

```javascript
const target = {
  name: "John Doe",
  age: 30
};

const handler = {
  get: function(obj, prop) {
    console.log(`Accessing property: ${prop}`);
    return obj[prop];
  }
};

const proxy = new Proxy(target, handler);

console.log(proxy.name);  // Logs: Accessing property: name
                          // Then logs: John Doe
console.log(proxy.age);   // Logs: Accessing property: age
                          // Then logs: 30
```

In this example, our Proxy intercepts all `get` operations on the target object and logs the property being accessed before returning its value.

## Validating Property Values with Proxies

Proxies can be used to add validation to object properties. Let's create a Proxy that ensures age is always a positive number:

```javascript
const person = {
  name: "Alice",
  age: 25
};

const validator = {
  set: function(obj, prop, value) {
    if (prop === 'age') {
      if (typeof value !== 'number') {
        throw new TypeError('Age must be a number');
      }
      if (value < 0) {
        throw new RangeError('Age must be a positive number');
      }
    }
    obj[prop] = value;
    return true;
  }
};

const validatedPerson = new Proxy(person, validator);

validatedPerson.age = 30;  // Works fine
validatedPerson.age = -5;  // Throws: RangeError: Age must be a positive number
validatedPerson.age = "30";  // Throws: TypeError: Age must be a number
```

This Proxy intercepts all `set` operations and applies validation rules when the 'age' property is being set.

## Creating "Private" Properties with Proxies

JavaScript doesn't have built-in private properties, but we can simulate them using Proxies:

```javascript
function createObjectWithPrivates(publicProps, privateProps) {
  return new Proxy(publicProps, {
    get(target, prop) {
      if (prop in target) {
        return target[prop];
      }
      throw new Error(`Access to private property "${prop}" is not allowed`);
    },
    set(target, prop, value) {
      if (prop in target) {
        target[prop] = value;
        return true;
      }
      throw new Error(`Setting private property "${prop}" is not allowed`);
    },
    has(target, prop) {
      return prop in target;
    }
  });
}

const obj = createObjectWithPrivates(
  { publicProp: "I'm public" },
  { privateProp: "I'm private" }
);

console.log(obj.publicProp);  // "I'm public"
console.log(obj.privateProp);  // Throws: Error: Access to private property "privateProp" is not allowed
```

This Proxy intercepts `get`, `set`, and `has` operations to prevent access to properties not explicitly defined in the public object.

## Revocable Proxies: The Self-Destructing Wrappers

JavaScript also provides revocable Proxies, which can be "turned off" when needed:

```javascript
const target = { secret: "I'm a secret" };
const { proxy, revoke } = Proxy.revocable(target, {
  get(target, prop) {
    console.log(`Accessing property: ${prop}`);
    return target[prop];
  }
});

console.log(proxy.secret);  // Logs: Accessing property: secret
                            // Then logs: I'm a secret

revoke();  // Revoke the Proxy

console.log(proxy.secret);  // Throws: TypeError: Cannot perform 'get' on a proxy that has been revoked
```

Revocable Proxies are useful in scenarios where you need to provide temporary access to an object and then completely cut off that access later.

## Performance Considerations

While Proxies are powerful, they do come with a performance overhead. Each operation that goes through the Proxy is slightly slower than performing the same operation directly on the target object. For most applications, this difference is negligible, but it's something to keep in mind for performance-critical code.

## Real-World Use Cases

Proxies can implement lazy loading of properties, which is useful for optimizing resource-intensive operations:

```javascript
const heavyResource = new Proxy({}, {
  get: (target, property) => {
    if (!(property in target)) {
      console.log(`Loading ${property}...`);
      target[property] = loadExpensiveResource(property);
    }
    return target[property];
  }
});

function loadExpensiveResource(key) {
  // Simulate an expensive operation
  return `Data for ${key}`;
}

console.log(heavyResource.user);  // Logs: Loading user... \n Data for user
console.log(heavyResource.user);  // Logs: Data for user (already loaded)
```

Proxies are perfect for implementing access control in objects, useful in creating secure or restricted environments:

```javascript
function createSecureObject(obj, allowedRoles) {
  return new Proxy(obj, {
    get: (target, prop) => {
      if (currentUserRole && allowedRoles.includes(currentUserRole)) {
        return target[prop];
      }
      throw new Error("Access denied");
    }
  });
}

let currentUserRole = 'User';
const secureData = createSecureObject({ secretKey: '1234' }, ['Admin']);

try {
  console.log(secureData.secretKey);
} catch (e) {
  console.log(e.message);  // Outputs: Access denied
}

currentUserRole = 'Admin';
console.log(secureData.secretKey);  // Outputs: 1234
```

## Conclusion

As we've seen, JavaScript Proxies offer a powerful way to intercept and customize operations on objects. Their real-world applications are vast, ranging from data binding and lazy loading to security features like input sanitization and access control.

By leveraging Proxies, you can create more robust, efficient, and secure applications. They allow you to add sophisticated behavior to objects without cluttering your codebase with repetitive logic.

Remember, while Proxies are powerful, they should be used judiciously. Always consider the performance implications and the potential for increased complexity in your code.

Now that you're armed with both the knowledge of how Proxies work and ideas for practical applications, why not try incorporating them into your next project? Happy coding, and may your objects always be well-guarded and highly functional!