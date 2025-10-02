# System Volume Control Using Hand Gestures

A Python-based application that allows you to control your system volume using hand gestures captured through your webcam. The application uses computer vision and hand tracking to detect the distance between your thumb and index finger, mapping it to system volume levels.

## Features

- **Real-time Hand Tracking**: Uses MediaPipe for accurate hand landmark detection
- **Gesture-based Volume Control**: Control volume by pinching your thumb and index finger together or apart
- **Visual Feedback**: See your hand landmarks and the connection line between thumb and index finger in real-time
- **Smooth Volume Adjustment**: Natural mapping of hand gesture distances to volume levels

## How It Works

The application captures video from your webcam and uses MediaPipe's hand tracking solution to detect hand landmarks. It specifically tracks:
- **Landmark 4**: Thumb tip
- **Landmark 8**: Index finger tip

The distance between these two points is calculated and mapped to system volume levels:
- **Hand gesture range**: 15-220 pixels
- **Volume range**: -63.5 dB to 0.0 dB (system volume range)

When you bring your thumb and index finger closer together, the volume decreases. When you move them apart, the volume increases.

## Requirements

This application requires the following Python packages:

- `opencv-python` - For video capture and image processing
- `mediapipe` - For hand tracking and landmark detection
- `numpy` - For numerical operations and interpolation
- `pycaw` - For Windows audio control
- `comtypes` - For COM interface handling

## Installation

1. **Clone the repository**:
   ```bash
   git clone https://github.com/johaankjis/system-volume-control.git
   cd system-volume-control
   ```

2. **Install the required dependencies**:
   ```bash
   pip install opencv-python mediapipe numpy pycaw comtypes
   ```

   Or create a requirements.txt file with the dependencies and install:
   ```bash
   pip install -r requirements.txt
   ```

## Usage

1. **Run the application**:
   ```bash
   python volume.py
   ```

2. **Control the volume**:
   - Position your hand in front of the webcam
   - Make a pinching gesture with your thumb and index finger
   - Move your fingers apart to increase volume
   - Bring your fingers closer together to decrease volume
   - The application will display a live video feed with hand landmarks and a line connecting your thumb and index finger

3. **Exit the application**:
   - Press `q` to quit

## Platform Support

**Note**: This application currently supports **Windows only** due to its dependency on the `pycaw` library, which uses Windows-specific audio APIs.

For macOS or Linux support, you would need to use alternative audio control libraries:
- **macOS**: Use `osascript` or `pycaw` alternatives
- **Linux**: Use `alsaaudio` or `pulsectl`

## Troubleshooting

### Webcam not detected
- Ensure your webcam is properly connected and not being used by another application
- Try changing the camera index in `cv2.VideoCapture(0)` to `1` or `2` if you have multiple cameras

### Hand not detected
- Ensure adequate lighting in your environment
- Keep your hand within the camera frame
- Try adjusting the distance between your hand and the camera

### Volume not changing
- Ensure you're running the application on Windows
- Check that your system audio is not muted
- Verify that you have proper permissions to control system audio

## Technical Details

The application uses:
- **OpenCV**: Captures video frames from the webcam
- **MediaPipe Hands**: Detects and tracks 21 hand landmarks in real-time
- **Pycaw**: Interfaces with Windows Core Audio APIs to control system volume
- **NumPy**: Performs linear interpolation to map gesture distance to volume levels

## Contributing

Contributions are welcome! Feel free to:
- Report bugs
- Suggest new features
- Submit pull requests

## License

This project is open source and available for educational and personal use.

## Acknowledgments

- Google's MediaPipe for the hand tracking solution
- The Pycaw project for Windows audio control
- OpenCV for computer vision capabilities
