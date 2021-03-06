Mixed-Up Code Exercises
------------------------

.. parsonsprob:: mixedupcode_12_1
        :numbered: left
        :practice: T
        :adaptive:

        Write a program to retrieve a file from 'http://data.pr4e.org/clown.txt' and print its contents using urllib.
        -----
        import urllib.request
        =====
        fhand = urllib.request.urlopen('http://data.pr4e.org/clown.txt')
        =====
        for line in fhand:
        =====
            words = line.decode().strip()
        =====
            print(words)

.. parsonsprob:: mixedupcode_12_2
        :numbered: left
        :practice: T 
        :adaptive:

        Write a program to retrive a file from 'http://data.pr4e.org/clown.txt' and save it to disk using urllib.
        -----
        import urllib.request, urllib.parse, urllib.error
        =====
        text = urllib.request.urlopen('http://data.pr4e.org/clown.txt').read()
        =====
        fhand = open('clown.txt', 'wb')
        =====
        fhand.write(text)
        =====
        fhand.close()

.. parsonsprob:: mixedupcode_12_3
        :numbered: left
        :practice: T
        :adaptive:

        Write a program that retrieves a file from 'http://data.pr4e.org/romeo.txt', saves it to disk first and then displays word count using urllib.
        -----
        import urllib.request
        =====
        text = urllib.Requests('http://data.pr4e.org/romeo.txt') #distractor
        =====
        text = urllib.request.urlopen('http://data.pr4e.org/romeo.txt')
        =====
        fhand = open('romeo.txt', wb)
        =====
        fhand.write(text)
        =====
        fhand.close()
        =====
        for line in text:
        =====
            words = line.decode().strip()
        =====
            for word in words:
        =====
                counts[word] = counts.get(word, 0) + 1
        =====
        print(counts)

.. parsonsprob:: mixedupcode_12_4
        :numbered: left
        :practice: T
        :adaptive:

        Write a program that retrieves an image file from 'http://data.pr4e.org/cover3.jpg' using urllib and save it to disk.
        -----
        import urllib.request, urllib.parse, urllib.error
        =====
        img = urllib.request.urlopen('http://data.pr4e.org/cover3.jpg').read()
        =====
        fhand = open('cover.jpg', 'wb')
        =====
        fhand.write(img)
        =====
        fhand.close()

.. parsonsprob:: mixedupcode_12_5
        :numbered: left
        :practice: T 
        :adaptive:

        Write a program that retrieves a text file from 'http://data.pr4e.org/romeo-full.txt' using urllib as several blocks of 100,000 characters, saves it to disk and prints the number of characters.
        -----
        import urllib.request, urllib.parse, urllib.error
        =====
        txt = urllib.request.urlopen('http://data.pr4e.org/romeo-full.txt')
        =====
        fhand = open('romeo-full.txt', 'wb')
        size = 0
        =====
        while True:
        =====
            info = txt.read(100000) 
        =====
            if len(info) < 1: break
        =====
            size = size + len(info)
        =====
            fhand.write(info)
        =====
        print(size, 'characters copied.')
        =====
        fhand.close()


.. parsonsprob:: mixedupcode_12_6
        :numbered: left
        :practice: T
        :adaptive:

        Write a program to retrieve a file from 'http://data.pr4e.org/romeo.txt' and print its contents using sockets.
        -----
        import socket
        =====
        mysock = socket.socket(socket.AF_INET, socket.SOCK_STREAM)
        =====
        mysock.connect(('data.pr4e.org', 80))
        =====
        cmd = 'GET http://data.pr4e.org/romeo.txt HTTP/1.0\r\n\r\n'.encode()
        =====
        mysock.send(cmd)
        =====
        while True:
        =====
            data = mysock.recv(512)
        =====
            if len(data) < 1: break
        =====
            print(data.decode(),end='')
        =====
            mysock.close()

.. parsonsprob:: mixedupcode_12_7
        :numbered: left
        :practice: T
        :adaptive:

        Write a program to retrieve all url links from 'www.nytimes.com' using regex and print them.
        -----
        import urllib.request, urllib.parse, urllib.error
        =====
        import re
        url = "https://www.nytimes.com/"
        =====
        html = urllib.request.urlopen(url).read()
        =====
        links = re.findall(b'href="(http[s]?://.*?)"', html)
        =====
        for link in links:
        =====
            print(link.decode())

.. parsonsprob:: mixedupcode_12_8
        :numbered: left
        :practice: T 
        :adaptive:

        Write a program to retrieve all url links from  'www.nytimes.com' using BeautifulSoup and print them.
        -----
        import urllib.request
        =====
        from bs4 import BeautifulSoup
        =====
        url = "https://www.nytimes.com/"
        =====
        html = urllib.request.urlopen(url).read()
        =====
        soup = BeautifulSoup(html, 'html.parser')
        =====
        tags = soup('a')
        =====
        for tag in tags:
        =====
            print(tag.get('href', None))

.. parsonsprob:: mixedupcode_12_9
        :numbered: left
        :practice: T 
        :adaptive:

        Write a program to retrieve all url links for images from  'www.nytimes.com' using BeautifulSoup and print them.
        -----
        import urllib.request
        =====
        from bs4 import BeautifulSoup
        =====
        url = "https://www.nytimes.com/"
        =====
        html = urllib.request.urlopen(url).read()
        =====
        soup = BeautifulSoup(html, 'html.parser')
        =====
        tags = soup('img')
        =====
        for tag in tags:
        =====
            print(tag.get('src', None))

.. parsonsprob:: mixedupcode_12_10
        :numbered: left
        :practice: T 
        :adaptive:

        Write a code that extracts data from several parts of the ‘a’ tag from “http://www.dr-chuck.com/page1.htm” using BeautifulSoup and print the tag, href, contents as well as all the attrs.
        -----
        from urllib.request import urlopen
        from bs4 import BeautifulSoup
        =====
        url = "http://www.dr-chuck.com/page1.htm"
        =====
        html = urlopen(url).read()
        =====
        soup = BeautifulSoup(html, "html.parser")
        =====
        tags = soup('a')
        =====
        for tag in tags:
        =====
            print('TAG:', tag)
            print('URL:', tag.get('href', None))
            print('Contents:', tag.contents[0])
            print('Attrs:', tag.attrs)
