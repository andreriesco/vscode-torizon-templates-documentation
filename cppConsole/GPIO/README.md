# GPIO C++ Sample Documentation #

Using the C++ console template from the Torizon VSCode Extension v2 - ApolloX,
to use the GPIOs follow this steps:

- Add the following command on the **Dockerfile.debug** file:

        RUN usermod -a -G gpio torizon

- Add the the necessary packages on the **torizonPackages.json** file, like this:

        {
            "deps": [
                "libgpiod2",
                "gpiod"
            ],

            "devDeps": [
                "libgpiod-dev:<desired-arch>",
                "libgpiod2:<desired-arch>"
            ]
        }

- Add the gpiochip corresponding to the application on the
**docker-compose.yml** file:

        volumes:
        - type: bind
            source: /dev/gpiochip0
            target: /dev/gpiochip0

- Modify the **main.cpp** file to toggle a GPIO, like this:

        int bank = <bank-number>;
        int line = <line-number>;

        ...GPIO Toggle...