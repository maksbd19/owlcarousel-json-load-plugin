This is a plguin to reconstruct the JSON data loading feature Owlcarousal had in version 1.3.

How to use it

params:
1. path: path to remote resource
2. onSuccess: callback function after the remote data is loaded
3. onError: callback function if there is any error while loading the remote data


Note: This plugin is still in a basic stage. You still need to manually add your slides and reinitialize the carousal
in your success callback. In future I do hope to remove all these limitations.
