# -*- encoding: utf-8 -*-

task :default => :configure

desc 'Configure mutt'
task :configure do
  env = {}

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

  if RUBY_PLATFORM =~ /darwin/
    if system '/bin/sh -c "command -v brew" &>/dev/null'
      env['CFLAGS' ] ||= ''
      env['LDFLAGS'] ||= ''
      %w[libidn gdbm].each do |pkg|
        prefix = %x(brew --prefix #{pkg}).chomp
        env['CFLAGS' ] << %Q( -I#{prefix}/include )
        env['LDFLAGS'] << %Q( -L#{prefix}/lib )
      end
    end
  end

  sh env, *cmd
end
