Write Code Exercises
---------------------
#.
    .. tabbed:: network_writecode1

      .. tab:: Question

          .. activecode:: network_writecode1q
              :language: python3

              Complete the following code that retrieves the file 'romeo.txt' from. Make changes to line 4 and 5.
              ~~~~
              import socket

              mysock = socket.socket(socket.AF_INET, socket.SOCK_STREAM)
              mysock.connect(('____', __))
              cmd = '____ ________________________ HTTP/1.0\r\n\r\n'.encode()
              mysock.send(cmd)

              while True:
                  data = mysock.recv(512)
                  if len(data) < 1:
                      break
                  print(data.decode(),end='')

              mysock.close()

      .. tab:: Answer

          .. activecode:: network_writecode1a
              :language: python3

              Complete the following code that retrieves the file 'romeo.txt' from. Make changes to line 4 and 5.
              ~~~~
              import socket

              mysock = socket.socket(socket.AF_INET, socket.SOCK_STREAM)
              mysock.connect(('data.pr4e.org', 80))
              cmd = 'GET http://data.pr4e.org/romeo.txt HTTP/1.0\r\n\r\n'.encode()
              mysock.send(cmd)

              while True:
                  data = mysock.recv(512)
                  if len(data) < 1:
                      break
                  print(data.decode(),end='')

                  mysock.close()



.. activecode:: writingcode_question12_2
        :language: python3

        Complete the following code to extract an image 'cover3.jpg' from the URL 'http://data.pr4e.org/cover3.jpg' and host 'data.pr4e.org'. There are 5 empty spaces.
        ~~~~

        import socket

        HOST = '________'
        PORT = 80
        mysock = socket.socket(socket.AF_INET, socket.SOCK_STREAM)
        mysock.connect((____, ____))
        mysock.sendall(b'___ __________________ HTTP/1.0\r\n\r\n')
        count = 0
        picture = b""

        while True:
            data = mysock.recv(5120)
            if len(data) < 1: break
            #time.sleep(0.25)
            count = count + len(data)
            print(len(data), count)
            picture = picture + data

        mysock.close()

        picture = picture[pos+4:]
        fhand = open("stuff.jpg", "wb")
        fhand.write(picture)
        fhand.close()

.. tabbed:: writecode_question12_3

    .. tab:: Question

        .. activecode:: writingcode_question12_3
                :language: python3

                Complete the following code that retrieves the text from 'http://data.pr4e.org/clown.txt', prints it and also prints the frequency of each word.
                ~~~~

                import urllib.request

                fhand = urllib.request.urlopen('_________________')


    .. tab:: Answer

        .. activecode:: writtencode_question12_3
                :language: python3

                Complete the following code that retrieves the text from 'http://data.pr4e.org/clown.txt' and prints the frequency of each word.
                ~~~~

                import urllib.request

                fhand = urllib.request.urlopen('http://data.pr4e.org/clown.txt')
                for line in fhand:
                    words = line.decode().strip()
                    print(words)
                    for word in words:
                        counts[word] = counts.get(word, 0) + 1
                print(counts)

.. activecode:: writingcode_question12_4
        :language: python3

        Write a program to retrieve and print text from 'http://data.pr4e.org/intro-short.txt" and print it.
        ~~~~

        import urllib.request

.. tabbed:: writecode_question12_5

    .. tab:: Question

        .. activecode:: writingcode_question12_5
                :language: python3

                Write a program to store image file from 'http://data.pr4e.org/cover.jpg'to your disk.
                ~~~~

                import urllib.request, urllib.parse, urllib.error

    .. tab:: Answer

        .. activecode:: writtencode_question12_5
                :language: python3

                Write a program to store image file from 'http://data.pr4e.org/cover.jpg'to your disk.
                ~~~~

                import urllib.request, urllib.parse, urllib.error

                img = urllib.request.urlopen('http://data.pr4e.org/cover.jpg').read()
                fhand = open('cover.jpg', 'wb')
                fhand.write(img)
                fhand.close()

.. activecode:: writingcode_question12_6
        :language: python3

        Complete the following program to extract all url from the webpage using regex.
        ~~~~

        import urllib.request, urllib.parse, urllib.error
        import re

        url = "https://www.nytimes.com"
        html = _______________________
        links = _______(b'href="(http[s]?://.*?)"', html)


.. tabbed:: writecode_question12_7

    .. tab:: Question

        .. activecode:: writingcode_question12_7
                :language: python3

                Write a program that retrives a txt file from 'https://www.gutenberg.org/files/1342/1342-0.txt' in several blocks of 100,000 characters, joins them and saves as 'prideandprejudice.txt' to disk and prints number of characters.
                ~~~~

                import urllib.request, urllib.parse, urllib.error

                txt = urllib.request.urlopen('___________________')

                size = 0
                while True:
                    info = txt.read(100000)
                    if len(info) < 1: break
                    size = size + len(info)

    .. tab:: Answer

        .. activecode:: writtencode_question12_7
                :language: python3

                Write a program that retrives a txt file from 'https://www.gutenberg.org/files/1342/1342-0.txt' in several blocks of 100,000 characters, joins them and saves as 'prideandprejudice.txt' to disk and prints number of characters.
                ~~~~

                import urllib.request, urllib.parse, urllib.error

                txt = urllib.request.urlopen('https://www.gutenberg.org/files/1342/1342-0.txt')
                fhand = open('prideandprejudice.txt', 'wb')
                size = 0
                while True:
                    info = txt.read(100000)
                    if len(info) < 1: break
                    size = size + len(info)
                    fhand.write(info)

                print(size, 'characters copied.')
                fhand.close()

.. activecode:: writingcode_question12_8
        :language: python3

        Write a program that retrives a txt file from 'https://www.gutenberg.org/files/16/16-0.txt' in several blocks of 100,000 characters, joins them and saves as 'peterpan.txt' to disk and prints number of characters.
        ~~~~

        import urllib.request, urllib.parse, urllib.error

.. tabbed:: writecode_question12_9

    .. tab:: Question

        .. activecode:: writingcode_question12_9
                :language: python3

                Complete the following code to print all the image sources from the webpage. Use 'img' and 'src' as tags.
                ~~~~

                import urllib.request
                from bs4 import BeautifulSoup

                url = "https://www.nytimes.com/"
                html = urllib.request.urlopen(url).read()
                soup = BeautifulSoup(html, 'html.parser')

    .. tab:: Answer

        .. activecode:: writtencode_question12_9
                :language: python3

                Complete the following code to print all the image sources from the webpage. Use 'img' and 'src' as tags.
                ~~~~

                import urllib.request
                from bs4 import BeautifulSoup

                url = "https://www.nytimes.com/"
                html = urllib.request.urlopen(url).read()
                soup = BeautifulSoup(html, 'html.parser')

                tags = soup('img')
                for tag in tags:
                    print(tag.get('src', None))


.. activecode:: writingcode_question12_10
        :language: python3

        Write a code that extracts data from several parts of the 'a' tag from "http://www.dr-chuck.com/page1.htm" using BeautifulSoup and html.parser and
        print the tag, href, contents as well as all the attrs.
        ~~~~

        import urllib.request
        from bs4 import BeautifulSoup
