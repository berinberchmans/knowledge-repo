---
description: The basics in running angular.
---

# Setting up an Angular project

### Installing angular CLI

First, we need to install the angular CLI. The code below will install the latest angular version globally.

```text
npm install -g @angular/cli
```

### Creating an angular application

Now, we need to create our angular app. Use the code below to initialize it. Replace "my-app" with the name you want to give your project. 

```text
ng new my-app
```

### Running the app

To run the app, go into the folder we have just created. In my case, its "my-app".

```text
cd my-app
```

Next, type the code to run the app. Please note this has to be run inside the project folder we created.

```text
ng serve
```

Then just go to [http://localhost:4200/](http://localhost:4200/) in your browser.

To automatically have the app run in our default browser when we run our project, add "-o" to the code.

```text
ng serve -o
```

Additionally, you can define the port address that you want to run the project in. This can be helpful when you are running more than one angular projects simultaneously.

```text
ng serve --port 4401    
```

Also, if you want to run the app in other devices other than the desktop such as mobile or tablets. You can try the below method.

The devices will need to be on the same local network, that is possibly to the same WIFI. You first will need to find your local IP address.

On Windows, type `ipconfig`  in the command prompt.

```text
ipconfig
```

On Mac, type `ifconfig |grep inet` in Terminal.

```text
ifconfig |grep inet
```

For more info on how to get the local IP address, see [this](https://lifehacker.com/how-to-find-your-local-and-external-ip-address-5833108). 

Once we have the IP address, use it in the following code. Replace "192.168.0.10" with your own IP address.

```text
ng serve --host 192.168.0.10.
```

Now you can open up **`http://your_IP_address:4200`** in a browser in your other devices.

