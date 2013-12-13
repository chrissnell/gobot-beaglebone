# gobot-beaglebone

Gobot (http://gobot.io/) is a library for robotics and physical computing using Go

This library provides an adaptor and driver for the Beaglebone Black (http://beagleboard.org/Products/BeagleBone+Black/)

## Getting Started

Install the library with: `go get -u github.com/hybridgroup/gobot-beaglebone`

## Example

```go
package main

import (
        "github.com/hybridgroup/gobot"
        "github.com/hybridgroup/gobot-beaglebone"
        "github.com/hybridgroup/gobot-gpio"
)

func main() {
        beaglebone := new(gobotBeaglebone.Beaglebone)
        beaglebone.Name = "beaglebone"

        led := gobotGPIO.NewLed(beaglebone)
        led.Name = "led"
        led.Pin = "P9_12"

        work := func() {
                gobot.Every("1s", func() { led.Toggle() })
        }

        robot := gobot.Robot{
                Connections: []interface{}{beaglebone},
                Devices:     []interface{}{led},
                Work:        work,
        }

        robot.Start()
}
```

## Documentation
We're busy adding documentation to our web site at http://gobot.io/ please check there as we continue to work on Gobot

Thank you!

## Contributing
In lieu of a formal styleguide, take care to maintain the existing coding style. Add unit tests for any new or changed functionality.

## License
Copyright (c) 2013 The Hybrid Group. Licensed under the Apache 2.0 license.
