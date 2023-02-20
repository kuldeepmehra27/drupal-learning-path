# Caching #

#### What is Caching? ####

Caching in Drupal is a technique used to speed up website performance by temporarily storing frequently accessed data. Drupal has several caching systems, including page caching, dynamic caching, asset caching, and cache tags. Caching can greatly improve website performance.

Cache API is used to store data that takes a long time to compute. Caching can either be permanent or valid only for a certain timespan, and the cache can contain any type of data.

The Cache system in Drupal provides the API needed to handle the creation, storage, and invalidation of cached data. From a storage perspective, it is extensible, allowing us to write our own custom cache backends **CacheBackendInterface**.

#### Dynamic Page Cache ####

Dynamic Page Cache is a caching system in Drupal that **caches personalized and dynamic content for authenticated users**. It enables Drupal to serve the cached version of the page for users who have already accessed it, thus saving processing power and improving website performance. It is enabled by default in Drupal but does not work with all types of personalized content. In cases where Dynamic Page Cache is not appropriate, other caching strategies like BigPipe or Edge Side Includes (ESI) may be more suitable.

#### Internal Page Cache ####

Internal Page Cache is a Drupal caching system that **caches entire pages for anonymous users**, resulting in significant performance improvements for websites with high traffic. It is enabled by default in Drupal 8 but can be configured or disabled if necessary. Internal Page Cache is suitable for static content that does not change frequently, but not for personalized or dynamic content. In those cases, other caching strategies like Dynamic Page Cache, BigPipe or Edge Side Includes (ESI) may be more appropriate.

#### Cacheability metadata ####

Cacheability metadata in Drupal is information that allows Drupal to determine how to cache and serve a page or component. It includes cache tags, cache contexts, and cache max-age, and is used to improve caching efficiency and reduce server load. Developers can add cacheability metadata using Drupal's caching API.

Cacheability metadata consists of 3 properties:
  - Cache tags
  - Cache contexts
  - Cache max-age

#### Cache tags ####

Cache tags in Drupal allow cached data to be associated with specific items, such as entities, users, or configurations. When an item is edited, and its content changes, the cached data becomes outdated and invalid. To ensure the cache reflects the updated data, developers should use cache tags to identify the dependencies of an item. For example, a node teaser has dependencies such as the node itself, the associated user entity, file entity, and text format. If any of these dependencies change, then the cached HTML for the node 5 teaser must be regenerated, and the cache tags would be ['node:5', 'user:3', 'file:4', 'config:filter.format.basic_html'].

Most data objects have a **::getCacheTags()** method that returns the associated tags. It is recommended that developers use this method rather than hardcoding tags. For example, **$node->getCacheTags()** would return node:5. If a developer is defining a custom data model or using something other than the Entity API or Configuration API, custom cache tags should be added and invalidated at the appropriate times.

[Read more about cache tags](https://www.drupal.org/docs/drupal-apis/cache-api/cache-tags)

#### Cache contexts ####

Cache contexts in Drupal vary the cache based on contextual information such as the day of the week, the user's last login date, or the value of a setting in the administrative UI. When determining cache contexts, you should ask yourself whether the thing being rendered varies based on contextual information. You can create your own context by defining a new tagged service. Cache contexts are implemented in classes that should implement the **\Drupal\Core\Cache\Context\CacheContextInterface**. An example of cache contexts in Drupal core is the teaser of a node that is rendered differently for users in different time zones.

[Read more about cache contexts](https://www.drupal.org/docs/drupal-apis/cache-api/cache-contexts)

#### Cache max-age ####

**Cache max-age varies the cache based on time**. For example, "Valid for 1 hour."

Max-age is a either a positive integer expressing a number of seconds, 0, or Cache::PERMANENT. Cache::PERMANENT is the default.

**0 means cachable for zero seconds, which is the same as saying not cacheable at all or disabled**. Use this to prevent an item from ever being cached.

**\Drupal\Core\Cache\Cache::PERMANENT** means cache forever, only invalidate based on cache tags.

[Read more about cache max-age](https://www.drupal.org/docs/drupal-apis/cache-api/cache-max-age)

#### Creating our own cache bin ####

In Drupal, a cache bin is a storage area for cached data, and it can be useful to create your own cache bin if you have specific caching needs.

To create your own cache bin, you can follow these steps:

1. Define a service for your cache bin in a custom module using the **services.yml** file.
2. In the service definition, specify the class that implements the **CacheBackendInterface** interface, which is used to interact with the cache backend.
3. Specify the cache backend and cache tag invalidation services that your cache bin should use.
4. Use the **CacheBackend get() and set()** methods to interact with your custom cache bin in your code.

![Custom cache service](/images/custom-cache-bin.png)
![Custom cache](/images/set-get-cache.png)

#### Invalidating cached items ####

Drupal core or other modules that vary on **max-age, tags, or contexts should already be invalidated automatically**. However, if you define custom cache tags, **you will need to define when they should be invalidated**, typically when the data they represent is updated. If you have custom methods like **$object->save() or $object->update()**, you can use them to invalidate cached items and ensure they are rebuilt the next time they are used.
```
\Drupal\Core\Cache\Cache::invalidateTags(['custom_object:1']);
```
Or via the cache_tags.invalidator service.
```
$this->container('cache_tags.invalidator')->invalidateTags(['custom_object:1']);
```

[Read more about cachebackend](https://api.drupal.org/api/drupal/core%21lib%21Drupal%21Core%21Cache%21CacheBackendInterface.php/interface/CacheBackendInterface/9.3.x#:~:text=interface%20CacheBackendInterface&text=Defines%20an%20interface%20for%20cache,cache%20identifiers%20are%20case%20sensitive.)

[Example](https://www.flocondetoile.fr/blog/cache-example-action-drupal-8)

:house: [Home Page](README.md) | [<< Previous Page](rest-api.md) | [Next Page >>](event-systems.md)
