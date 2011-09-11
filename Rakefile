# -*- ruby -*-

# clean tasks
require 'rake/clean'
CLEAN.add('*.out', '*.aux', '*.log')
CLOBBER.add('*.pdf')

# Tex
TEX   = 'xelatex'
PDFX3 = '-output-driver="xdvipdfmx -q -E -V 3"'

# Books and cover
BOOK_BLURB  = 'book-blurb.pdf'
COVER_BLURB = 'cover-blurb.pdf'
BOOK_WEB    = 'book-web.pdf'

# Photos
PHOTOS_WEB   = FileList['photos.web/*.jpg']
PHOTOS_BOOK = FileList['photos.book/*.jpg']


# Task to create web book
PHOTOS_WEB.each { |photo| file BOOK_WEB => photo }

desc "Create the PDF for the web version of the book"
file BOOK_WEB => ['book-web.tex', 'common-book.tex', 'fonts.tex', 'colors.tex'] do
  sh %{#{TEX} book-web.tex}
end

# Tasks to create blurb book
PHOTOS_BOOK.each { |photo| file BOOK_BLURB => photo }

desc "Create the PDF for the blurb version of the book"
file BOOK_BLURB => ['book-blurb.tex', 'common-book.tex', 'fonts.tex', 'colors.tex'] do
  sh %{#{TEX} #{PDFX3} book-blurb.tex}
end

desc "Create the PDF for the cover of the blurb version of the book"
file COVER_BLURB => ['cover-blurb.tex', 'common-book.tex', 'fonts.tex', 'colors.tex'] do
  sh %{#{TEX} #{PDFX3} cover-blurb.tex}
end
