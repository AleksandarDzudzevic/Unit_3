## Python code 
```.py 
class MovieDownloader:
    def __init__(self, download_speed):
        if download_speed <= 0:
            raise ValueError("Download speed needs to be more than 0")
        self.download_speed = download_speed

    def calculate_download_time(self, movie_size):
        if movie_size <= 0:
            raise ValueError("Movie size needs to be more than 0")
        download_time_seconds = movie_size / (self.download_speed * 1024 * 1024)
        print(download_time_seconds)
        minutes, seconds = divmod(download_time_seconds, 60)
        return f"{int(minutes)} minutes {int(seconds)} seconds"

```
## Python testing code 
```.py
import pytest
from quiz052 import MovieDownloader

def test_calculate_download_time():
    downloader = MovieDownloader(download_speed=10)
    movie_size = 1500 * 1024 * 1024  # 1500 MB
    assert downloader.calculate_download_time(movie_size) == "2 minutes 30 seconds"

    downloader = MovieDownloader(download_speed=5)
    movie_size = 500 * 1024 * 1024  # 500 MB
    assert downloader.calculate_download_time(movie_size) == "1 minutes 40 seconds"

def test_download_speed_validation():
    with pytest.raises(ValueError, match=r"Download speed must be greater than 0"):
        downloader = MovieDownloader(download_speed=0)
    with pytest.raises(ValueError, match=r"Download speed must be greater than 0"):
        downloader = MovieDownloader(download_speed=-10)

def test_movie_size_validation():
    downloader = MovieDownloader(download_speed=10)
    with pytest.raises(ValueError, match=r"Movie size must be greater than 0"):
        downloader.calculate_download_time(0)
    with pytest.raises(ValueError, match=r"Movie size must be greater than 0"):
        downloader.calculate_download_time(-100)
```
## Proof
![](https://github.com/AleksandarDzudzevic/Unit_3/blob/main/quiz052test.png)
