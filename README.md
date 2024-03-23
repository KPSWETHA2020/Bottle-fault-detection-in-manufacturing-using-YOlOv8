# Bottle-fault-detection-in-manufacturing-using-YOlOv8
import cv2
from ultralytics import YOLO
from matplotlib import pyplot as plt
from IPython.display import clear_output

# Load the YOLOv8 model
model = YOLO("/content/best.pt")

# Open the video file
video_path = "/content/(14) Plastic bottle manufacturing process - explained by UpSkul - YouTube - Google Chrome 2024-03-22 17-11-09.mp4"
cap = cv2.VideoCapture(video_path)
# Get the video frame width, height, and frames per second (fps)
frame_width = int(cap.get(cv2.CAP_PROP_FRAME_WIDTH))
frame_height = int(cap.get(cv2.CAP_PROP_FRAME_HEIGHT))
fps = int(cap.get(cv2.CAP_PROP_FPS))
 
SEC-  DEPARTMENT OF AIDS –  4- 1 –PROJECTWORK1– slide# -‹#›
 
 
 

Important Code segments

# Define the codec and create VideoWriter object
fourcc = cv2.VideoWriter_fourcc(*'MP4V')  # Define the codec for the output video
output_video_path = "/content/output_video.mp4"  # Path to save the output video
out = cv2.VideoWriter(output_video_path, fourcc, fps, (frame_width, frame_height))

# Loop through the video frames
while cap.isOpened():
    # Read a frame from the video
    success, frame = cap.read()

    if success:
        # Run YOLOv8 tracking on the frame, persisting tracks between frames
        results = model.track(frame, persist=True,conf=0.3)

        # Visualize the results on the frame
        annotated_frame = re
