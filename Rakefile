require 'rubygems'
require 'kramdown'

task :default do
  book = "<html><head><meta name='cover' content='cover.jpg'><title>Forty Grand</title></head><body>"
  Dir.chdir('chapters/01-Part-One')
  Dir.glob("[0-9][0-9]*.mkd").each do |filename|
    markdown = File.read(filename)
    html = Kramdown::Document.new(markdown).to_html
    book += html
    book += "<mbp:pagebreak/>"
  end
  book += "</body></html>"
  Dir.chdir('../..')
  File.open('FortyGrand.html', 'w') {|f| f.write(book)}
  `kindlegen FortyGrand.html`
end

task :pdf do
  book = ""
  Dir.chdir('chapters/01-Part-One')
  Dir.glob("[0-9][0-9]*.mkd").each do |filename|
    markdown = File.read(filename)
    latex = Kramdown::Document.new(markdown).to_latex
    book += latex
  end
  Dir.chdir('../..')
  File.open('FortyGrand.tex', 'w') {|f| f.write(book)}
end
