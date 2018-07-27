# coding: utf-8
task :default => :generate

desc 'Create new post with rake "post[post-name]"'
task :p, [:title] do |t, args|
  if args.title then
    new_post(args.title, '_posts')
  else
    puts 'rake "p[post-name]"'
  end
end

def new_post(title, place)
  time = Time.now
  filename = "#{place}/" + time.strftime("%Y-%m-%d-") + title + '.markdown'
  if File.exists? filename then
    puts "Post already exists: #{filename}"
    return
  end
  date = `date '+%Y-%m-%d %H:%M:%S %z' | tr -d "\n"`
    
  File.open(filename, "wb") do |f|
    f << <<-EOS
---
title: #{title}
layout: post
date: #{date}
category: 
---


EOS
  %x[echo "#{filename}" | pbcopy]
  end
  puts "created #{filename}"
  # `git add #{filename}`
  # `open -a Byword #{filename}`
  # `el #{filename}`
end
