# Face_recognition.ipynb
The provided Python code uses the face_recognition and OpenCV libraries to perform real-time face recognition on a video (input.mp4). It detects faces, compares them with known faces, and labels them accordingly, then generates an output video (output.avi) with labeled recognized faces.
Here's a breakdown of the code:

1. **Importing Libraries:**
   - The code starts by importing the necessary libraries: `face_recognition` for face detection and recognition, and `cv2` (OpenCV) for video processing and visualization.

2. **Video Processing and Face Recognition:**

   - **Opening Input Video (2.1):** The input video named "input.mp4" is loaded using OpenCV's `VideoCapture` class. The total number of frames in the video is obtained using `CAP_PROP_FRAME_COUNT`.

   - **Creating Output Video (2.2):** An output video named "output.avi" is created using the `VideoWriter` class from OpenCV. The video codec used is MPEG-4 with a frame rate of approximately 23.98 frames per second (fps), and the resolution of the frames is set to (1280, 538).

   - **Providing Sample Images for Face Recognition (2.3):** Two sample images ("ryan.jpeg" and "steve.jpeg") are loaded using `face_recognition` and their face encodings are calculated using `face_encodings` function. These encodings will be used as the reference for recognizing faces.

   - **Initializing Variables (2.4):** Variables are initialized to keep track of detected face locations, encodings, recognized face names, and frame number.

   - **Face Detection and Recognition (2.5):** A loop runs to process each frame of the input video:
   
     - The current frame is read from the input video.
     - The frame is converted from BGR to RGB format, which is used by the `face_recognition` library.
     - Faces are detected in the RGB frame using `face_locations`.
     - Face encodings are computed using `face_encodings`.
     - For each detected face encoding, the code compares it with the known face encodings to recognize the person using `compare_faces`. If a match is found, the person's name is assigned ("Ryan" or "Steve"). If no match is found, the name is set as "Unknown".
     
   - **Visualizing Results (2.5):** The code labels the recognized faces by drawing rectangles around them and displaying their names below the rectangles using OpenCV's drawing functions.
   
   - **Writing Output Video (2.5):** Each processed frame is written to the output video with the added bounding boxes and labels. The progress of frame processing is printed.

3. **Memory Release (2.6):**
   - After processing all frames, the input video is released to free up system resources.
