const imageUpload = document.getElementById('imageUpload');
const horizontalDimensionInput = document.getElementById('horizontalDimension');
const horizontalUnitSelect = document.getElementById('horizontalUnit');
const verticalDimensionInput = document.getElementById('verticalDimension');
const verticalUnitSelect = document.getElementById('verticalUnit');
const paperSizeSelect = document.getElementById('paperSize');
const processButton = document.getElementById('processButton');
const progressBar = document.querySelector('.progress-bar');
const originalImage = document.getElementById('originalImage');
const khakaImage = document.getElementById('khakaImage');
const downloadButton = document.getElementById('downloadButton');

imageUpload.addEventListener('change', (event) => {
  const file = event.target.files[0];
  const reader = new FileReader();

  reader.onload = (e) => {
    originalImage.src = e.target.result;
  };

  reader.readAsDataURL(file);
});

processButton.addEventListener('click', () => {
  // Implement image processing logic here
  // Example: Using a service (replace with your actual service)
  // fetch('https://api.example.com/convert', {
  //   method: 'POST',
  //   body: JSON.stringify({
  //     image: originalImage.src,
  //     // Add other parameters like dimensions, units, paper size
  //   })
  // })
  // .then(response => response.json())
  // .then(data => {
  //   khakaImage.src = data.khakaImageUrl; // Assuming the API returns the khaka image URL
  // })
  // .catch(error => {
  //   console.error('Error processing image:', error);
  //   // Display an error message to the user
  // });

  // Simulate progress bar animation
  let progress = 0;
  const interval = setInterval(() => {
    progress += 10;
    progressBar.style.width = `${progress}%`;

    if (progress >= 100) {
      clearInterval(interval);
    }
  }, 500);

  // Convert Image to Khaka (Edge Detection)
  const canvas = document.createElement('canvas');
  const context = canvas.getContext('2d');
  const img = new Image();
  img.onload = function() {
    canvas.width = img.width;
    canvas.height = img.height;
    context.drawImage(img, 0, 0);
    const imageData = context.getImageData(0, 0, canvas.width, canvas.height);
    // Perform edge detection (replace with your desired algorithm)
    // Example: Simple edge detection
    for (let i = 0; i < imageData.data.length; i += 4) {
      // Calculate the average color value
      const avg = (imageData.data[i] + imageData.data[i + 1] + imageData.data[i + 2]) / 3;
      // Set the pixel to black or white based on threshold
      const threshold = 128; // Adjust for desired contrast
      if (avg < threshold) {
        imageData.data[i] = 0;
        imageData.data[i + 1] = 0;
        imageData.data[i + 2] = 0;
      } else {
        imageData.data[i] = 255;
        imageData.data[i + 1] = 255;
        imageData.data[i + 2] = 255;
      }
    }
    context.putImageData(imageData, 0, 0);
    khakaImage.src = canvas.toDataURL();
  };
  img.src = originalImage.src;
});

downloadButton.addEventListener('click', () => {
  const link = document.createElement('a');
  link.href = khakaImage.src; // Assuming khakaImage.src contains the khaka image URL
  link.download = 'khaka.png'; // Set the desired filename for the download
  link.click();
});
