require "bundler/setup"

task :default => [:list]

desc "Lists all the tasks."
task :list do
  puts "Tasks: \n- #{(Rake::Task.tasks).join("\n- ")}"
end

desc "Checks for required dependencies."
task :check do
  environemnt_vars = [
    'OPSCODE_USER',
    'OPSCODE_ORGNAME',
    'KNIFE_CLIENT_KEY_FOLDER',
    'KNIFE_VALIDATION_KEY_FOLDER',
    'KNIFE_CHEF_SERVER',
    'KNIFE_COOKBOOK_COPYRIGHT',
    'KNIFE_COOKBOOK_LICENSE',
    'KNIFE_COOKBOOK_EMAIL',
    'KNIFE_CACHE_PATH'
  ]
  errors = []
  environemnt_vars.each do |var|
    if ENV[var].nil?
      errors.push(" - \e\[31m#Variable: {var} not set!\e\[0m\n")
    else
      puts " - \e\[32mVariable: #{var} set to \"#{ENV[var]}\"\e\[0m\n"
    end
  end

  # client_key               "#{ENV['HOME']}/.chef/#{user}.pem"
  # validation_client_name   "#{ENV['ORGNAME']}-validator"
  # validation_key           "#{ENV['HOME']}/.chef/#{ENV['ORGNAME']}-validator.pem"
  # chef_server_url          "https://api.opscode.com/organizations/#{ENV['ORGNAME']}"


  file_list = [
    "#{ENV['KNIFE_CLIENT_KEY_FOLDER']}/#{ENV['OPSCODE_USER']}.pem",
    "#{ENV['KNIFE_VALIDATION_KEY_FOLDER']}/#{ENV['OPSCODE_ORGNAME']}-validator.pem",
  ]

    file_list.each do |file|
      if File.exist?(file)
        puts " - \e\[32mFile: \"#{file}\" found.\e\[0m\n"
      else
        errors.push(" - \e\[31mRequired file \"#{file}\" not found!\e\[0m\n")
      end
    end

  unless errors.empty?
    puts "The following errors occured:\n#{errors.join()}"
  end
end

desc "Builds the package."
task :build do
  puts "Nothing to do yet..."
end

desc "Fires up the Vagrant box."
task :start do
  puts "Nothing to do yet..."
end