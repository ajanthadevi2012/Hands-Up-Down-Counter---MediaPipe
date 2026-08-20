# 🙆 Hands Up/Down Counter using MediaPipe Pose and OpenCV

A real-time pose-based movement counting application built using **Python, OpenCV, and MediaPipe**.

This project captures video from a webcam, detects the user's body pose, monitors the positions of both wrists, identifies **hands up** and **hands down** movements, counts completed up-to-down movements, displays the movement count and current status, shows the GitHub source link in the top-right corner, and records the processed output as a video.

---

## 🚀 Features

- 🎥 Real-time webcam input
- 🧍 Full-body pose detection using MediaPipe Pose
- ✋ Detects left and right wrist positions
- 📊 Calculates the average vertical position of both hands
- 🙆 Detects when both hands are raised
- 🙇 Detects when the hands move down
- 🔢 Counts completed hands up/down movements
- 🟢 Displays the current **UP/DOWN** status
- 🔗 Draws pose landmarks and body connections
- 🪞 Provides a mirror-view webcam display
- 🔗 Displays the GitHub source link in the top-right corner
- 🎬 Records the processed output
- 💾 Saves the output video in the current project folder
- ⌨️ Press `Q` to stop the application

---

## ▶️ How to Run

Clone the repository:

```bash
git clone https://github.com/ajanthadevi2012
```

Move to the project folder:

```bash
cd YOUR_PROJECT_FOLDER
```

Install the required libraries:

```bash
pip install opencv-python mediapipe
```

Run the program:

```bash
python hands_up_down_counter.py
```

---

## 📥 Input

The application uses the system webcam as the input source:

```python
cap = cv2.VideoCapture(0)
```

The webcam continuously captures frames and sends them to MediaPipe Pose for body landmark detection.

---

## ⚙️ Processing Workflow

The application performs the following steps:

1. Capture a frame from the webcam.
2. Flip the frame horizontally to create a mirror view.
3. Convert the frame from **BGR to RGB**.
4. Process the frame using **MediaPipe Pose**.
5. Detect body landmarks.
6. Extract the positions of the **left wrist** and **right wrist**.
7. Calculate the average vertical position of both hands.
8. Detect when the hands move above the defined **UP threshold**.
9. Detect when the hands move below the defined **DOWN threshold**.
10. Count one completed movement when the hands move from **UP to DOWN**.
11. Draw the pose landmarks and body connections.
12. Display the movement count.
13. Display the current **UP/DOWN** status.
14. Display the GitHub source link in the top-right corner.
15. Save the processed frame to the output video.

---

## 📏 Movement Detection Logic

The project uses the normalized vertical (`y`) coordinates of both wrists.

The average hand position is calculated as:

```python
hands_y = (left_wrist.y + right_wrist.y) / 2
```

### Hands Up

The hands are considered **UP** when:

```python
hands_y < up_thres
```

Default threshold:

```python
up_thres = 0.35
```

### Hands Down

A movement is counted when the hands were previously detected as **UP** and then move below the down threshold:

```python
if hands_up and hands_y > down_thres:
    count += 1
    hands_up = False
```

Default threshold:

```python
down_thres = 0.65
```

This prevents the counter from continuously increasing while the hands remain in the same position.

---

## 🧍 Pose Landmarks

MediaPipe Pose detects body landmarks representing different parts of the body, including:

- Head
- Shoulders
- Elbows
- Wrists
- Hips
- Knees
- Ankles

This project primarily uses the following landmarks:

- `LEFT_WRIST`
- `RIGHT_WRIST`

The detected pose landmarks and body connections are displayed in the output window.

---

## 📤 Output

The application displays a real-time output window containing:

- Webcam video
- Body pose landmarks
- Pose connections
- Movement count
- Current UP/DOWN status
- GitHub source link

Example:

```text
Folds: 5
Status: UP
```

The processed output is automatically saved as:

```text
hands_up_down_counter_output.mp4
```

The output video is stored in the **current project folder**.

---

## ⌨️ Controls

| Key | Action |
|---|---|
| `Q` | Stop the webcam and save the output video |

---

## 📁 Project Structure

```text
Hands-Up-Down-Counter/
│
├── hands_up_down_counter.py
├── README.md
└── hands_up_down_counter_output.mp4
```

---

## 🔗 GitHub Source

The GitHub link displayed in the top-right corner of the live output and recorded video is:

```python
github_link = "https://github.com/ajanthadevi2012"
```

GitHub Profile:

https://github.com/ajanthadevi2012

---

## 🛠️ Technologies Used

- Python
- OpenCV
- MediaPipe

---

## 👩‍💻 Author

**Dr. Ajantha Devi**

📧 Email: ap3solutionsresearch@gmail.com

🔗 GitHub: https://github.com/ajanthadevi2012

🔗 LinkedIn: https://in.linkedin.com/ajantha-devi-vairamani-a253a8217/

▶️ YouTube: https://www.youtube.com/@DemystifywithAjay

---

⭐ If you find this project useful, consider giving the repository a **star**!

Happy Learning! 🚀
