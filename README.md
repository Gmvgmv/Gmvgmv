- 👋 Hi, I’m @Gmvgmv
- 👀 I’m interested in ...
- 🌱 I’m currently learning ...
- 💞️ I’m looking to collaborate on ...
- 📫 How to reach me ...

<!---
Gmvgmv/Gmvgmv is a ✨ special ✨ repository because its `README.md` (this file) appears on your GitHub profile.
You can click the Preview link to take a look at your changes.
--->
import cv2
import numpy as np

# Function to generate random live data
def generate_live_data():
    temperature = np.random.randint(-10, 30)
    humidity = np.random.randint(0, 100)
    # You can add more data fields as needed

    return temperature, humidity

# Function to generate a video frame using the live data
def generate_video_frame(temperature, humidity):
    image = cv2.imread("background_image.jpg")  # Load a background image
    cv2.putText(image, f"Temperature: {temperature}°C", (10, 50), cv2.FONT_HERSHEY_SIMPLEX, 1, (0, 0, 255), 2)
    cv2.putText(image, f"Humidity: {humidity}%", (10, 100), cv2.FONT_HERSHEY_SIMPLEX, 1, (0, 0, 255), 2)
    # Add more data to the image as needed

    return image

# Function to generate the live video
def generate_live_video():
    video_writer = cv2.VideoWriter('live_video.mp4', cv2.VideoWriter_fourcc(*'MP4V'), 30, (640, 480))

    while True:
        temperature, humidity = generate_live_data()
        frame = generate_video_frame(temperature, humidity)
        video_writer.write(frame)
        cv2.imshow('Live Video', frame)
        if cv2.waitKey(1) & 0xFF == ord('q'):
            break

    video_writer.release()
    cv2.destroyAllWindows()

# Call the function to start generating the live video
generate_live_video()
