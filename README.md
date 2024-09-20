# Auto Clicker Bot for karate kido Telegram Desktop 

## Overview

This project is a Python-based automation script that uses the **mss** library to capture the screen and **OpenCV** for image recognition. The script performs automatic clicks using **pyautogui** when specific patterns or objects are detected within a designated area of the screen. The primary goal of the script is to detect objects (e.g., wood logs) and simulate a clicking action accordingly, alternating between left and right directions.

https://github.com/user-attachments/assets/575c3b5a-9af2-47bd-b73a-ce4599946153


## Key Features

- **Screen Capture**: Utilizes the `mss` library to capture screen regions for object detection.
- **Object Detection**: Uses **OpenCV**'s template matching (`cv2.matchTemplate`) to detect specific patterns within captured screenshots.
- **Auto Clicking**: Simulates mouse clicks based on detected objects using **pyautogui**.
- **Dynamic Clicking**: Alternates between clicking on the left and right sides of the screen based on detected object patterns.

## Libraries and Dependencies

The project uses the following Python libraries:

- **mss**: For capturing screenshots of specific screen regions.
- **OpenCV** (`cv2`): For template matching and image manipulation.
- **numpy**: For efficient array manipulation of image data.
- **pyautogui**: To simulate mouse clicks and other automated user interactions.
- **random**: To add some randomness to the click timing, simulating more human-like behavior.




You can install the required libraries using:

```bash
pip install mss opencv-python numpy pyautogui
```

## Project Structure

- `short_right.jpg`, `short_left.jpg`, `long_right.jpg`, `long_left.jpg`: Template images used for object detection.
- `main.py`: The main script for running the auto-clicker bot.
  
## How It Works

1. **Screen Regions**: The script defines two regions on the screen where it looks for objects (left and right).
   - Left region coordinates: `(820, 565, 135, 100)`
   - Right region coordinates: `(970, 565, 135, 100)`

2. **Object Detection**: The script uses **OpenCV** to perform template matching with predefined images (`short_right.jpg`, `short_left.jpg`, `long_right.jpg`, `long_left.jpg`).
   - If the matching score exceeds a threshold (0.68), it considers the object as detected.

3. **Click Simulation**: When an object is detected, the script alternates between clicking on the left or right side of the screen at specified coordinates:
   - Left click coordinates: `(860, 700)`
   - Right click coordinates: `(1045, 700)`

4. **Dynamic Clicking**: After each detected object, the script dynamically switches between left and right regions for further object detection.

## How to Use

1. **Prepare Images**: Ensure that the `short_right.jpg`, `short_left.jpg`, `long_right.jpg`, and `long_left.jpg` images are present in the root directory. These should be images of the objects you want the script to detect.

2. **Run the Script**: Once everything is set up, run the `main.py` script. After a 3-second delay, the script will start capturing screen regions and detecting objects.
   
   ```bash
   python main.py
   ```

3. **Exit**: To exit the script, close the OpenCV window displaying the screenshots.

## Customization

- **Regions**: You can modify the `dimensions_left` and `dimensions_right` dictionaries to capture different screen regions if the default coordinates do not match your screen setup.
- **Thresholds**: The matching threshold for object detection can be adjusted by modifying the `max_val_short` and `max_val_long` comparison values (currently set to `0.68`).
- **Coordinates**: Change the `x` and `y` values in the `pyautogui.click` function to simulate clicks at different screen locations.

## Known Issues and Considerations

- **Performance**: The script continuously captures screen regions and performs image matching, which may be resource-intensive on some systems.
- **Matching Accuracy**: Depending on the quality and size of the template images, the matching process may require fine-tuning to avoid false positives or negatives.
- **Screen Resolution**: Ensure that your screen resolution is 1920x1080 - open the app in telegram desktop
- **Closing Out**: Due to the rapid screen grabbing  - break key is hard to implement - use CTRL ALT DEL to stop the code

## License

This project is open-source and available under the MIT License.

---

Feel free to contribute to the project by submitting issues, suggesting features, or opening pull requests on the GitHub repository!

---

### Example of command to run the script:

```bash
python main.py
``` 

