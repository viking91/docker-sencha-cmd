# Build from Dockerfile
docker build -t sencha-cmd .


# Example commands to create cordova app
docker run --rm -v $(pwd):/code --workdir /code sencha-cmd cordova init com.example.app MyApp
docker run --rm -v $(pwd):/code --workdir /code sencha-cmd app build
docker run --rm -v $(pwd):/code --workdir /code sencha-cmd build native


# Run Android application on device connected with USB
docker run -it --rm --privileged -v /dev/bus/usb:/dev/bus/usb -v $(pwd)/cordova:/code --workdir /code sencha-cmd cordova run android

# For faster build cache gradle on local machine
docker run -it --rm --privileged -v /dev/bus/usb:/dev/bus/usb -v ~/.gradle:/root/.gradle -v $(pwd)/cordova:/code --workdir /code --entrypoint=/opt/node/bin/cordova sencha-cmd run android

docker run -it --rm --privileged -v /dev/bus/usb:/dev/bus/usb -v ~/.gradle:/root/.gradle -v $(pwd)/cordova:/code --workdir /code --entrypoint=/opt/node/bin/cordova sencha-cmd platform add android
