# -*- encoding: utf-8 -*-

task :default => :configure

desc 'Configure mutt'
task :configure do
  cmd = %W[
    ./prepare
    --prefix=#{ENV['PREFIX'] || '/opt/mutt'}
    --enable-gpgme
    --disable-pgp
    --enable-smime
    --enable-smtp
    --enable-exact-address
    --enable-hcache
    --disable-full-doc
    --with-regex
    --with-ssl
    --with-sasl
    --with-gdbm
    --with-idn
  ]

  cmd << '--enable-debug' if ENV['DEBUG'] == '1'

  sh *cmd
end
