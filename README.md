# Google Images Scraper

This script uses Selenium to scrape images from Google Images based on a search query. It allows the user to download a specified number of images and saves them to a local folder.

## Prerequisites

Before running the script, ensure you have the following installed:
- Python 3.x
- [Selenium](https://pypi.org/project/selenium/)
- [Pillow](https://pypi.org/project/Pillow/)
- [requests](https://pypi.org/project/requests/)

You also need the Microsoft Edge WebDriver. Download it from [Microsoft Edge Driver] and place it in a directory, for example, `C:/edgedriver_win64/msedgedriver.exe`.

## Installation

1. Clone this repository or download the script file.

2. Install the required Python libraries:
 
   pip install selenium pillow requests

## How It Works

1. **Initialize WebDriver:**
   The script starts by initializing the Microsoft Edge WebDriver using the provided path to the `msedgedriver.exe`. This WebDriver instance is used to control the Edge browser.

2. **Open Google Images:**
   It opens Google Images with the search query provided by the user. The URL is constructed with the query parameter to perform an image search.

3. **Load Page and Retrieve Thumbnails:**
   After navigating to the search results page, the script waits for the thumbnails to load. This delay is handled using `time.sleep()` to ensure that the images have time to appear on the page.

4. **Validate Thumbnails:**
   The script locates all thumbnail images using their class names and validates whether the number of available thumbnails meets the user's request. If there are fewer thumbnails than requested, it adjusts the number of images to download.

5. **Download Images:**
   For each thumbnail:
   - The script scrolls to the thumbnail and clicks it to open the full-size image.
   - It waits for the full-size image to load.
   - It retrieves the URL of the full-size image and performs an HTTP GET request to download the image.
   - The image is saved in a local folder named `pics`, with a filename that includes the search query and the image’s sequence number.

## Troubleshooting

- **Images Not Downloading Properly:**
  If images are not downloading as expected:
  - **Check Class Names:** Ensure that the class names used in the script to identify thumbnails and full-size images match those on the Google Images page. The class names can change over time, requiring updates to the script.
  - **Inspect Page Elements:** Use the browser’s developer tools to inspect the page elements and verify the correct class names and element selectors.

- **Script Execution Issues:**
  If the script fails to run or encounters errors:
  - **Verify WebDriver Path:** Check that the path to `msedgedriver.exe` specified in the script is correct and points to the actual location of the WebDriver executable on your system.
  - **Check WebDriver Version:** Ensure that the version of Edge WebDriver matches the version of the Microsoft Edge browser installed on your machine. Mismatches can cause compatibility issues.
  - **Update WebDriver:** If needed, download the appropriate version of Edge WebDriver from [Microsoft Edge Driver](https://developer.microsoft.com/en-us/microsoft-edge/tools/webdriver/) and update the path in the script.

If you continue to encounter issues, consider consulting the [Selenium documentation](https://www.selenium.dev/documentation/en/) or seeking help from the developer community.

