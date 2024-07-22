# Tiphop
Social media is 
/<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Video Feed</title>
<style>
    body {
        font-family: Arial, sans-serif;
        background-color: #f0f0f0;
        margin: 0;
        padding: 20px;
    }
    .container {
        max-width: 800px;
        margin: 0 auto;
        background-color: #fff;
        padding: 20px;
        box-shadow: 0 0 10px rgba(0,0,0,0.1);
    }
    .video {
        display: flex;
        margin-bottom: 20px;
        padding: 10px;
        background-color: #f9f9f9;
        border-radius: 5px;
    }
    .video img {
        width: 120px;
        height: 90px;
        object-fit: cover;
        border-radius: 5px;
        margin-right: 10px;
    }
    .video-content {
        flex: 1;
    }
    .video-title {
        font-size: 18px;
        font-weight: bold;
        margin-bottom: 5px;
    }
    .video-description {
        font-size: 14px;
        color: #666;
        margin-bottom: 10px;
    }
    .video-author {
        font-size: 14px;
        color: #888;
    }
</style>
</head>
<body>
<div class="container">
    <div class="video">
        <img src="video-thumbnail.jpg" alt="Video Thumbnail">
        <div class="video-content">
            <div class="video-title">Example Video Title</div>
            <div class="video-description">Lorem ipsum dolor sit amet, consectetur adipiscing elit. Sed gravida lectus vel nisl efficitur consectetur.</div>
            <div class="video-author">Uploaded by: John Doe</div>
        </div>
    </div>
    <div class="video">
        <img src="another-video-thumbnail.jpg" alt="Video Thumbnail">
        <div class="video-content">
            <div class="video-title">Another Example Video Title</div>
            <div class="video-description">Pellentesque habitant morbi tristique senectus et netus et malesuada fames ac turpis egestas.</div>
            <div class="video-author">Uploaded by: Jane Smith</div>
        </div>
    </div>
    <!-- Add more videos as needed -->
</div>
</body>
</html>
// Example React Native component for video feed
import React, { useEffect, useState } from 'react';
import { View, Text, FlatList, StyleSheet } from 'react-native';
import VideoThumbnail from './VideoThumbnail';

const VideoFeedScreen = () => {
  const [videos, setVideos] = useState([]);

  useEffect(() => {
    // Fetch videos from backend API
    fetch('https://your-backend-api/videos')
      .then(response => response.json())
      .then(data => setVideos(data))
      .catch(error => console.error('Error fetching videos', error));
  }, []);

  return (
    <View style={styles.container}>
      <FlatList
        data={videos}
        renderItem={({ item }) => (
          <VideoThumbnail video={item} />
        )}
        keyExtractor={item => item.id}
      />
    </View>
  );
};

const styles = StyleSheet.create({
  container: {
    flex: 1,
    justifyContent: 'center',
    alignItems: 'center',
    padding: 10,
  },
});

export default VideoFeedScreen;
