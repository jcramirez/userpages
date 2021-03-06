[Golang] Read Lines From File or String
#######################################

:date: 2016-04-06T22:51+08:00
:modified: 2018-04-09T06:06+08:00
:tags: Go, Golang, String Manipulation, File Input/Output, Read Lines
:category: Go
:summary: Readlines_ from string or file in Go_ programming language.
:og_image: http://www.unixstickers.com/image/cache/data/stickers/golang/Go-brown-side.sh-600x600.png
:adsu: yes

.. contents:: `Read lines`_ from string or file in Golang_.

----

Readlines From String
+++++++++++++++++++++

.. rubric:: `Run Code on Go Playground <https://play.golang.org/p/BwtBPE-d8mU>`__
   :class: align-center

.. code-block:: go

  import (
  	"bufio"
  	"strings"
  )

  func StringToLines(s string) (lines []string, err error) {
  	scanner := bufio.NewScanner(strings.NewReader(s))
  	for scanner.Scan() {
  		lines = append(lines, scanner.Text())
  	}
  	err = scanner.Err()
  	return
  }

.. adsu:: 2

Readlines From File
+++++++++++++++++++

.. code-block:: go

  import (
  	"bufio"
  	"os"
  )

  func FileToLines(filePath string) (lines []string, err error) {
  	f, err := os.Open(filePath)
  	if err != nil {
  		return
  	}
  	defer f.Close()

  	scanner := bufio.NewScanner(f)
  	for scanner.Scan() {
  		lines = append(lines, scanner.Text())
  	}
  	err = scanner.Err()
  	return
  }

.. adsu:: 3

----

Tested on: ``Ubuntu Linux 15.10``, ``Go 1.6``.

----

References:

.. [1] `golang read lines from file - Google search <https://www.google.com/search?q=golang+read+lines+from+file>`_

.. [2] | `go string to line - Google search <https://www.google.com/search?q=go+string+to+line>`_
       | `go readline - Google search <https://www.google.com/search?q=go+readline>`_
       | `Example (Lines) - bufio - The Go Programming Language <https://golang.org/pkg/bufio/#example_Scanner_lines>`_
       | `Example (Custom) - bufio - The Go Programming Language <https://golang.org/pkg/bufio/#example_Scanner_custom>`_

.. [3] `os - The Go Programming Language <https://golang.org/pkg/os/>`_

.. [4] `fmt - The Go Programming Language <https://golang.org/pkg/fmt/>`_

.. [5] `strings - The Go Programming Language <https://golang.org/pkg/strings/>`_

.. [6] `[Golang] Read Lines From URL <{filename}../../../2017/02/02/go-readlines-from-url%en.rst>`_


.. _Go: https://golang.org/
.. _Golang: https://golang.org/
.. _os: https://golang.org/pkg/os/
.. _Create: https://golang.org/pkg/os/#Create
.. _fmt: https://golang.org/pkg/fmt/
.. _Fprintf: https://golang.org/pkg/fmt/#Fprintf
.. _Read lines: https://www.google.com/search?q=Read+lines
.. _Readlines: https://www.google.com/search?q=Readlines
.. _Go Playground: https://play.golang.org/
