# -*- ruby -*-

require 'rake/clean'

# Some useful constant
CLEAN.add('*.out', '*.aux', '*.log')
CLOBBER.add('*.pdf')
TEX = 'xelatex'
ARGS = '-output-driver="xdvipdfmx -q -E -V 3"'
BOOK_BLURB = 'book-blurb.pdf'
COVER_BLURB = 'cover-blurb.pdf'
BOOK_WEB = 'book-web.pdf'

# Task to create web book
FileList['photos.web/*.jpg'].each {|photo| file BOOK_WEB => photo}

desc "Create the PDF for the web version of the book"
file BOOK_WEB => ['book-web.tex', 'common-book.tex', 'fonts.tex'] do
  sh %{#{TEX} book-web.tex}
end

# Tasks to create blurb book
FileList['photos.blurb/*.jpg'].each {|photo| file BOOK_BLURB => photo}

desc "Create the PDF for the blurb version of the book"
file BOOK_BLURB => ['book-blurb.tex', 'common-book.tex', 'fonts.tex'] do
  sh %{#{TEX} #{ARGS} book-blurb.tex}
end

desc "Create the PDF for the cover of the blurb version of the book"
file COVER_BLURB => ['cover-blurb.tex', 'common-book.tex', 'fonts.tex'] do
  sh %{#{TEX} #{ARGS} cover-blurb.tex}
end
