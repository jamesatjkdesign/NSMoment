namespace :test do
  task :prepare do
  end

  desc "Run the NSMoment Tests for iOS"
  task :ios => :prepare do
    $ios_success = system("xctool test -workspace Tests/NSMomentTests.xcworkspace -scheme 'iOSTests' -sdk iphonesimulator ONLY_ACTIVE_ARCH=NO")
  end

  desc "Run the NSMoment Tests for Mac OS X"
  task :osx => :prepare do
    $osx_success = system("xctool test -workspace Tests/NSMomentTests.xcworkspace -scheme 'OSXTests' -sdk macosx ONLY_ACTIVE_ARCH=NO")
  end
end

desc "Run the NSMoment Tests for iOS & Mac OS X"
task :test => ['test:ios', 'test:osx'] do
  puts "\033[0;31m! iOS unit tests failed" unless $ios_success
  puts "\033[0;31m! OS X unit tests failed" unless $osx_success
  if $ios_success && $osx_success
    puts "\033[0;32m** All tests executed successfully"
  else
    exit(-1)
  end
end

task :default => 'test'
