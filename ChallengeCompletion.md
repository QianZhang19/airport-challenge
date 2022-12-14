# Airport Challenge

This software is used to control the flow of planes at an airport

## User Stories

```
As an air traffic controller
So I can get passengers to a destination
I want to instruct the airport to land a plane

As the system designer
So that the software can be used for many different airports
I would like a default airport capacity that can be overridden as appropriate

As an air traffic controller
To ensure safety
I want to prevent landing when the airport is full

As an air traffic controller
So I can get passengers on the way to their destination
I want to instruct the airport to let a plane take off and confirm that it is no longer in the airport

As an air traffic controller
To avoid confusion
I want to prevent asking the airport to let planes take-off which are not at the airport, or land a plane that's already landed

As an air traffic controller
To ensure safety
I want to prevent takeoff when weather is stormy

As an air traffic controller
To ensure safety
I want to prevent landing when weather is stormy

As an air traffic controller
To count planes easily
Planes that have landed must be at an airport
```

## Domain Models

### User Story 1

```
As an air traffic controller
So I can get passengers to a destination
I want to instruct the airport to land a plane
```

#### Domain Model

| Objects | Properties                  | Messages     | Output |
| ------- | --------------------------- | ------------ | ------ |
| Airport | airportPlanes@Array[@plane] | land(@plane) | @void  |
| Plane   | planeID@Plane               | land()       | @void  |

#### Tests
1. Test if a plane is landed at the airport when land is called with plane

---

## User Story 2

```
As the system designer
So that the software can be used for many different airports
I would like a default airport capacity that can be overridden as appropriate
```

#### Domain Model

| Objects | Properties                  | Messages             | Output |
| ------- | --------------------------- | -------------------- | ------ |
| Airport | airportPlanes@Array[@plane] | setCapacity(@number) | @void  |

#### Tests
1. Test if a default airport capacity can be overridden as appropriate

---

## User Story 3

```
As an air traffic controller
To ensure safety
I want to prevent landing when the airport is full
```

#### Domain Model

| Objects | Properties                  | Messages | Output   |
| ------- | --------------------------- | -------- | -------- |
| Airport | airportPlanes@Array[@plane] | isFull() | @Boolean |
| Plane   | planeID@Plane               | isFull() | @Boolean |

#### Tests
1. Test if the plane landing is prevented when the airport is full

---

## User Story 4

```
As an air traffic controller
So I can get passengers on the way to their destination
I want to instruct the airport to let a plane take off and confirm that it is no longer in the airport
```

#### Domain Model

| Objects | Properties                  | Messages               | Output   |
| ------- | --------------------------- | ---------------------- | -------- |
| Airport | airportPlanes@Array[@plane] | send(@plane)           | @void    |
|         |                             | takeoffConfirm(@plane) | @Boolean |
| Plane   | planeID@Plane               | send()                 | @void    |
|         |                             | takeoffConfirm()       | @Boolean |

#### Tests
1. Test if the plane is taken off from the airport when send is called
2. Test the confirmation is given when the plane has been taken off

---

## User Story 5

```
As an air traffic controller
To avoid confusion
I want to prevent asking the airport to let planes take-off which are not at the airport, or land a plane that's already landed
```

#### Domain Model

| Objects | Properties                  | Messages           | Output   |
| ------- | --------------------------- | ------------------ | -------- |
| Airport | airportPlanes@Array[@plane] | planeHasTakenOff() | @Boolean |
|         |                             | planeHasLanded()   | @Boolean |
|         |                             |                    |          |
| Plane   | planeID@Plane               | planeHasTakenOff() | @Boolean |
|         |                             | planeHasLanded()   | @Boolean |

#### Tests
1. Test if prevent letting a plane take off when they are not at the airport
2. Test if prevent landing a plane when that's already landed

---

## User Story 6

```
As an air traffic controller
To ensure safety
I want to prevent takeoff when weather is stormy
```

#### Domain Model

| Objects | Properties                  | Messages           | Output   |
| ------- | --------------------------- | ------------------ | -------- |
| Airport | airportPlanes@Array[@plane] | stormyTakeOff()    | @Boolean |
| Plane   | planeID@Plane               | stormyTakeOff()    | @Boolean |
| Weather | Weather@stormy              | weathergenerator() | @Boolean |
|         |                             | stormyTakeOff()    | @Boolean |

#### Tests
1. Test if prevent takeoff when weather is stormy

---

## User Story 7

```
As an air traffic controller
To ensure safety
I want to prevent landing when weather is stormy
```

#### Domain Model

| Objects | Properties                  | Messages           | Output   |
| ------- | --------------------------- | ------------------ | -------- |
| Airport | airportPlanes@Array[@plane] | stormyLand()       | @Boolean |
| Plane   | planeID@Plane               | stormyLand()       | @Boolean |
| Weather | Weather@stormy              | weathergenerator() | @Boolean |
|         |                             | stormyLand()       | @Boolean |

#### Tests
1. Test if prevent landing when weather is stormy

---

## User Story 8

```
As an air traffic controller
To count planes easily
Planes that have landed must be at an airport
```

#### Domain Model

| Objects | Properties                  | Messages         | Output   |
| ------- | --------------------------- | ---------------- | -------- |
| Airport | airportPlanes@Array[@plane] | countAirplanes() | @Boolean |
| Plane   | planeID@Plane               | countAirplanes() | @number  |

#### Tests
1. Test if planes that have landed at an airport

---
## Executing program

### Steps
how to run the tests:
* Install project dependencies by using `npm install` command
* Develop Domain Model by reading User Stories
* Create a test folder containing specification and testing-framework files
* Create a property file containing messages
* Start to run the first test
* Start to run the next tests

### Methods
how you approached the problem:
* land() - land a plane
* setCapacity() - set a default airport capacity for use for many different airports
* isFull() - determine if airport is full
* send() - take off a plane
* takeoffConfirm() - confirmation of taking off a plane
* planeHasTakenOff() - prevent taking off if the plane is not at the airport
* planeHasLanded() - prevent landing if the plane is at the airport
* weathergenerator() - generate a random weather condition
* stormyTakeOff() - prevent takeoff when the weather is stormy
* stormyLand() - prevent land when the weather is stormy
* countAirplanes() - make sure the plane land at the same airport

### Error
1. 'MODULE_NOT_FOUND'
![Alt text](errors/cantFindModule.png)

2. TypeError: airport.land is not a function
![Alt text](errors/noFunc.png)

3. SyntaxError: Unexpected token '.'
![Alt text](errors/UnexpectedToken.png)

4. ReferenceError: airportPlanes is not defined
![Alt text](errors/notDefined.png)

5. false test1
![Alt text](errors/testFalse.png)

6. false test2
![Alt text](errors/testFalse2.png)

7. Max is not defined
![Alt text](errors/maxNotDefined.png)

## Authors

Qian Zhang

## Acknowledgments
* Lucas Chagas
* Chung Yan Ho
