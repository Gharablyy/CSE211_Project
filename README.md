# Mbed OS Real-Time Clock and Voltmeter with 7-Segment Display

This project is part of the Introduction to Embedded CSE211s Course at Ain Shams University. It implements a real-time clock and a simple voltmeter, displaying information on a 4-digit 7-segment display controlled via a shift register.

## Hardware Requirements

* **Microcontroller Board:** NUCLEO-F401RE (or a compatible Mbed OS board)
* **Shield:** Arduino Multifunction Shield (featuring a 4-digit 7-segment display driven by a shift register, buttons, and a potentiometer).

The project utilizes the following components on the Arduino Multifunction Shield:
* 4-digit 7-segment display (connected via a shift register)
* Button S1 (connected to pin A1) for timer reset
* Button S3 (connected to pin A3) for switching display mode
* Potentiometer (connected to pin A0) for analog voltage input

## Project Setup

This project is developed using Mbed OS and can be built with Mbed Studio or other compatible Mbed OS build tools.

**Using Mbed Studio:**

1.  Open Mbed Studio.
2.  Go to `File > Open Mbed Program...`.
3.  Navigate to and select the folder containing this project's files.
4.  Ensure your target board (NUCLEO-F401RE) is selected in Mbed Studio.

**Using Mbed CLI (Alternative):**

1.  Ensure you have Mbed CLI installed: [Install Mbed CLI](https://os.mbed.com/docs/mbed-os/latest/quick-start/offline-with-mbed-cli.html)
2.  Clone this repository (or import it) if you haven't already.
    ```bash
    git clone <your-repository-url>
    cd <your-project-folder>
    ```
    (Replace `<your-repository-url>` and `<your-project-folder>` with your actual project details).

## Application Functionality

The application performs the following tasks:

1.  **Real-Time Clock (RTC):** By default, the 4-digit 7-segment display shows the elapsed time in MM:SS format. The timer increments every second using a `Ticker`. The maximum display time is 99 minutes and 59 seconds.
2.  **Timer Reset:** Pressing Button S1 (connected to A1) resets the displayed timer back to 00:00.
3.  **Analog Voltage Display:** Pressing and holding Button S3 (connected to A3) switches the display mode. The 7-segment display will show the current voltage reading from the potentiometer (connected to A0) in Volts, with two decimal places (e.g., 3.30).
4.  **Minimum/Maximum Voltage Tracking:** The program continuously tracks the minimum and maximum voltage values read from the potentiometer since the board was last reset or powered on. (Note: While the code tracks min/max, the current display logic only shows the *current* voltage when S3 is pressed. You could extend the project to display min/max as well).
5.  **Display Switching:** When Button S3 is released, the display automatically switches back to showing the elapsed time. The RTC continues to run in the background even when the voltage is displayed.

The 7-segment display is controlled by shifting out data to a shift register, which drives the individual segments and digits.

## Building and Running

1.  Connect your NUCLEO-F401RE board to your computer using a USB cable.
2.  In **Mbed Studio**:
    * Click the **Build** button (hammer icon) to compile the project.
    * Click the **Run** button (play icon) to flash the compiled program onto your connected board.
3.  **Using Mbed CLI**:
    * Open your terminal in the project directory.
    * Run the compile and flash command, replacing `<TARGET>` with your board name (e.g., `NUCLEO_F401RE`) and `<TOOLCHAIN>` with your toolchain (e.g., `GCC_ARM`).
        ```bash
        mbed compile -m <TARGET> -t <TOOLCHAIN> --flash
        ```
    * Alternatively, manually copy the generated `.bin` file from the `./BUILD/<TARGET>/<TOOLCHAIN>/` directory to the Mbed board's USB drive.

## Expected Behavior

* Upon power-up or reset, the 7-segment display should show `00:00` and start counting seconds and minutes.
* Pressing S1 should reset the display to `00:00`.
* Pressing and holding S3 should show the voltage from the potentiometer on the display (e.g., `3.30`). Rotating the potentiometer knob should change the displayed voltage.
* Releasing S3 should return the display to showing the elapsed time.

## Troubleshooting

* Ensure your board is correctly connected and recognized by your computer and Mbed Studio.
* Verify that the Arduino Multifunction Shield is properly seated on the Nucleo board.
* Check the pin connections in the code (`D4`, `D7`, `D8` for the shift register; `A1`, `A3` for buttons; `A0` for the potentiometer) match how the shield is connected to the Nucleo.
* Refer to the Mbed OS documentation for general troubleshooting: [Mbed OS Handbook](https://os.mbed.com/docs/mbed-os/latest/introduction/index.html)

## Related Links

* [Mbed OS Documentation](https://os.mbed.com/docs/mbed-os/latest/introduction/index.html)
* [Mbed OS API References (DigitalOut, DigitalIn, AnalogIn, Ticker, ThisThread)](https://os.mbed.com/docs/mbed-os/latest/apis/index.html)
* [NUCLEO-F401RE resources](https://os.mbed.com/platforms/ST-Nucleo-F401RE/)
* Information on Shift Registers (e.g., 74HC595) and 7-segment displays might be helpful resources, depending on the specific components on your shield.

---

This README provides a good starting point. You can further enhance it by:
* Adding photos of your hardware setup (perhaps in the `resources` folder you mentioned earlier).
* Including a Fritzing diagram or pinout diagram showing the connections.
* Explaining the shift register driving logic in more detail if desired.
* Adding a section on how to extend the project (e.g., displaying min/max voltage, adding more features).
## Demo file.gif
![Project Demonstration](resources/Project_Running.gif)

## Better Quality Video
Watch the full video at higher quality of the project fromvhere: [Project Demo Video](https://drive.google.com/drive/u/1/folders/1XyMBgWulXaC0YtWTRtJL3cCQBkWPy9cO?dmr=1&ec=wgc-drive-hero-goto)