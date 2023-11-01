class Car:
    def __init__(self, make, model):
        self.make = make
        self.model = model
        self.speed = 0
        self.engine_status = False

    def start_engine(self):
        if not self.engine_status:
            print("Starting the engine.")
            self.engine_status = True
        else:
            print("Engine is already running.")

    def stop_engine(self):
        if self.engine_status:
            print("Stopping the engine.")
            self.engine_status = False
            self.speed = 0
        else:
            print("Engine is already off.")

    def accelerate(self, mph):
        if self.engine_status:
            self.speed += mph
            print(f"Accelerating to {self.speed} mph.")
        else:
            print("Engine is off. Can't accelerate.")

    def brake(self, mph):
        if self.speed >= mph:
            self.speed -= mph
            print(f"Braking to {self.speed} mph.")
        else:
            print("Can't brake below 0 mph.")

    def status(self):
        print(f"Car: {self.make} {self.model}")
        print(f"Engine: {'Running' if self.engine_status else 'Off'}")
        print(f"Speed: {self.speed} mph")

if __name__ == "__main__":
    my_car = Car("Toyota", "Camry")

    while True:
        print("\nCar Control Menu:")
        print("1. Start Engine")
        print("2. Stop Engine")
        print("3. Accelerate")
        print("4. Brake")
        print("5. Check Status")
        print("6. Exit")

        choice = input("Enter your choice: ")

        if choice == "1":
            my_car.start_engine()
        elif choice == "2":
            my_car.stop_engine()
        elif choice == "3":
            mph = int(input("Enter acceleration speed (mph): "))
            my_car.accelerate(mph)
        elif choice == "4":
            mph = int(input("Enter braking speed (mph): "))
            my_car.brake(mph)
        elif choice == "5":
            my_car.status()
        elif choice == "6":
            print("Exiting the car control app.")
            break
        else:
            print("Invalid choice. Please try again.")
