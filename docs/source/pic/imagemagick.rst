imagemagick
==============


图片四周加空白
--------------------

        convert -background white -gravity center -quality 9 -extent 1200x900  input.png output.png


图片质量
----------

        convert -strip -quality 80 input.jpeg output.jpeg
