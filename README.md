# map_TS

# Recap about JS Class

A Class is like a structure defining how an Object will look like (Property)
and what can it do (Method)

We can assign a value to it directly by doing the normal way like

```
class Car {
  constructor() {
    this.color = 'red';
  }
}
```

but with TS we need to specify the type of the value in side an Object as well
so it will looke something like this

```
class Car {
 color : string
 constructor() {
    this.color = 'red';
  }
}
```

also with Method we must specify what will that method return

```
  carColor(): string {
    return this.color;
  }
```

# constructor()

This is the part where you create or give a property or a method the value
it can be anything. Take a look at Company.ts

```
  constructor() {
    this.companyName = faker.company.name();
    this.catchPhrase = faker.company.catchPhrase();
    this.location = {
      lat: faker.location.latitude(),
      lng: faker.location.longitude(),
    };
  }
```

As you can see we give a value by using the faker library, you can even just type in the number as well

But this constructor can also take in an argument like in CustomMap.ts

```
  constructor(divId: string) {
    this.googleMap = new google.maps.Map(
      document.getElementById(divId) as HTMLElement,
      {
        zoom: 3,
        center: {
          lat: 0,
          lng: 0,
        },
      }
    );
  }
```

Here we are taking in a arugument name divId which is a string
THEN we use it to get element by ID
This will happen on the step we create the customMap using this CustomMap class
like below

```
const customMap = new CustomMap("map")
```

now doing this will allow us to know that the "map" parse in to the class
will go to the constructor function with the name "divID" (the order matters) and
eventually be used as an id to getEelementById

# implements

In Company.ts we import Mapable interface from CustomMap
Which this Mapable is used in CustomMap's method
Then in Company.ts we use Mappable to with the class Company

```
export class Company implements Mapable
```

This help TS check whether the class constructor Company
is following the Mapable interface
Which this Company class will eventually be used as an argument for the CustomMap method
This will also help us check 1 more step ahead making sure the Company and be pass in to CustomMap

#
