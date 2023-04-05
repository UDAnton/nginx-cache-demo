## How to run a demo
1. Run ```docker-compose up``` to start Nginx.
2. Send two times GET request to http://localhost:8080/image1.jpg and check response headers that X-Cache-Status = MISS. 
Here we'll get image1.jpg from server.
![Alt text](/test/first-get-image-request-1.png?raw=true "Response image")
![Alt text](/test/first-get-image-request-2.png?raw=true "Response headers")
![Alt text](/test/second-get-image-request-1.png?raw=true "Response image")
![Alt text](/test/second-get-image-request-2.png?raw=true "Response headers")
3. Send third time GET request to http://localhost:8080/image1.jpg and check response headers that X-Cache-Status = HIT. 
Here we'll get image1.jpg from cache.
![Alt text](/test/third-get-image-request-1.png?raw=true "Response image")
![Alt text](/test/third-get-image-request-2.png?raw=true "Response headers")
4. Let's swap(rename image2 to image1 and image1 to image2) our images in folder.
5. Send GET request to http://localhost:8080/image1.jpg and check response headers that X-Cache-Status = HIT and image isn't changed. 
Here we'll get image1.jpg from cache, but actual image1.jpg was swapped to image2.jpg in server.
![Alt text](/test/get-image-request-from-cache-1.png?raw=true "Response image")
![Alt text](/test/get-image-request-from-cache-2.png?raw=true "Response headers")
6. Send GET request to http://localhost:8080/image1.jpg with 'Cache-Purge: true' header
and check response headers that X-Cache-Status = BYPASS and image1.jpg is changed to image2.jpg.
![Alt text](/test/get-image-request-from-server-1.png?raw=true "Response image")
![Alt text](/test/get-image-request-from-server-2.png?raw=true "Response headers")
