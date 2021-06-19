# Face-Similarity-On-BioID_DB

## Dataset


We have used [Bio_ID Dataset](https://www.bioid.com/uploads/BioID-FaceDatabase-V1.2.zip). The dataset consists of 1521 gray level images with a resolution of 384×286 pixel. Each one shows the frontal view of a face of one out of 23 different test persons. 

1. **Model1** - Unsupervised Method for face similarity.
	
Used HaarCascade Classifier for face detection.Since images are mostly the frontal view of a face so didn't used any face alignment technique for straightening of image face.
Once face is detected face is cropped from image and passed through Facenet pre-trained model to extract face embedding of 128-d.
Used cosine similarity method to calculate similarity between different embeddings.If cosine similarity is above 0.5 then images are similar.

2. **Model2** - Haarcascade + Softmax

The dataset was unlabeled so I have applied unsupervised learning using kmeans to get the data labeled data.
I have been assigned to use HaarCascade Classifier but since it has some drawbacks - It expects the face to be fully contained in the image and even if a small portion of the face is missing, it fails out. And I don't want to add noisy data so I have removed the images that are not processed by HaarCascade. But it is unaffordable to loose any image in such a small dataset, hence to consider all the images, I have used another face detection approach by Dlib.

3. **Model3** - Dlib + Softmax


Although dlib pipeline doesn't performed well on validation data but didn't got the time to test it robustly.

4. **Model4** - Haarcascade_+_CNN_+_Triplet_Loss

In this model we have used triplet loss instead of softmax function because it is a way to learn good embeddings for each face of the dataset. In the sense of embedded spaceing, faces from the same person should be close together and form well separated clusters. 
