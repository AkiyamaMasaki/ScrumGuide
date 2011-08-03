# -*- coding: utf-8 -*-
task :make_html do
  ["ScrumGuide_ja.hiki", "ScrumGuide2_ja.hiki"].each do |file|
    html = file.gsub(/\.hiki/, '') + ".html"
    `hikidoc --no-wikiname #{file} > _build/#{html}`
    content = ''
    open("_build/#{html}", "r+") do |f|
      content = f.read.gsub(/[\r\n]/, '').gsub(/(<\/.+?>)/, "\\1\n")
    end
    content.gsub!(/<\/head>/,
                  '<meta http-equiv="Content-Type" content="text/html; charset=utf-8">' + "\n" +
                  '<link rel="stylesheet" href="./style.css" type="text/css">' + "\n" +
                  '</head>')
    open("_build/#{html}", "w+") do |f|
      f.write(content)
    end
  end
end
