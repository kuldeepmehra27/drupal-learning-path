# Event Systems #

#### Hooks vs Events ####

Hooks are functions that are called at specific points in the code execution, while events are classes that define how the system should react to specific events. 

- **Implementation:** Hooks are implemented as functions that are called at specific points in the code execution, while events are implemented as classes that define how the system should react to specific events.
- **Triggering:** Hooks are triggered by the execution of specific functions, while events are triggered by the occurrence of specific events.
- **Coordination:** Events are more coordinated than hooks, with multiple subscribers able to listen to the same event and respond in a coordinated way, while hooks can sometimes lead to conflicts between modules if multiple modules implement the same hook.
- **Flexibility:** Hooks offer a higher degree of flexibility than events, allowing for a wide range of modifications and customizations, while events provide a more structured and standardized way of extending the system.

**Event Subscribers:** An Event Subscriber or Listener in Drupal is a **callable method or function that reacts to specific events being propagated throughout the Event Registry**. It allows developers to customize the behavior of Drupal in a structured and standardized way by responding to various events, such as user logins, node creations, form submissions, and system errors.

**Event Registry:** The Event Registry is a central database in Drupal that maintains a record of all available events and Event Subscribers. It is part of the Event Dispatcher system and is responsible for matching triggered events with the appropriate Event Subscribers. It is a critical component that enables developers to create structured and standardized custom Event Subscribers to respond to specific events in the system.

**Event Dispatcher(trigger):** "dispatch" refers to the process of triggering and spreading an event throughout a system. The purpose of this mechanism is to coordinate the behavior of different components or subsystems in response to the event. The specifics of the dispatch mechanism vary depending on the system and the event being dispatched.

#### Use cases of Event Subscribers ####

- Use Drupal Rules to send notification emails to users with editor role on creation of node marked for review by writer role.
- Use hook system to react to user creation event in custom module.
- Use Drupal Comment Notify module to send email to commenter when their comment is published.
- Use Drupal Event API to define and trigger custom events for other modules to listen and react to.
- Use Drupal routing system to define URL paths and their corresponding controllers, not events.

#### getSubscribedEvents() ####
getSubscribedEvents() is a method in Drupal 8/9 that can be implemented by a class that implements the **EventSubscriberInterface**. This method is used to define which events the class is interested in and how the class should react to those events. The method returns an array of event names and corresponding method names that should be called when those events occur. This allows Drupal to automatically register the event subscriber with the Symfony event dispatcher and call the corresponding method when an event that the subscriber has subscribed to is triggered.

Reference: https://www.drupal.org/docs/creating-modules/subscribe-to-and-dispatch-events

:house: [Home Page](README.md) | [<< Previous Page](caching.md) | [Next Page >>](plugins.md)
