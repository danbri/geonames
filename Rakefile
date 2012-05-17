require 'rake'
require 'rake/clean'

CLEAN.include ["*.nt"]

#Download the data dump
task :download do
  sh %{wget -O all-geonames-rdf.zip http://download.geonames.org/all-geonames-rdf.zip}
end

# Unpack the data dump
task :unpack do
  puts "Unpacking"
  sh %{unzip all-geonames-rdf.zip}
end

#Convert the dump format into ntriples
task :convert do
 sh %{ruby geonames.rb all-geonames-rdf.txt geonames.nt} 
end

#Zip up the ntriples
task :package do
 sh %{gzip geonames.nt}
end

task :publish => [:download, :convert, :package]
