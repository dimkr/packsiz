# this file is part of packsiz.
#
# Copyright (c) 2017 Dima Krasner
#
# Permission is hereby granted, free of charge, to any person obtaining a copy
# of this software and associated documentation files (the "Software"), to deal
# in the Software without restriction, including without limitation the rights
# to use, copy, modify, merge, publish, distribute, sublicense, and/or sell
# copies of the Software, and to permit persons to whom the Software is
# furnished to do so, subject to the following conditions:
#
# The above copyright notice and this permission notice shall be included in all
# copies or substantial portions of the Software.
#
# THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR
# IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY,
# FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE
# AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER
# LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM,
# OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN
# THE SOFTWARE.

project('packsiz', 'c', version : '0.0.1', license : 'MIT')

subproject('szl',
           default_options: ['builtin_all=true', 'with_float=false', 'with_zlib=no', 'with_tls=no', 'with_ffi=no', 'with_lzfse=no', 'with_zstd=no', 'with_test=no', 'with_oop=no', 'with_server=no', 'with_server=no', 'with_resp=no', 'with_http=no', 'with_https=no'])

cfg = configuration_data()
bindir = get_option('bindir')
cfg.set('prefix', get_option('prefix'))
cfg.set('bindir', bindir)
cfg.set('sysconfdir', get_option('sysconfdir'))
cfg.set('localstatedir', get_option('localstatedir'))

packsiz = configure_file(input:
                         'packsiz.in',
                         output: 'packsiz',
                         configuration: cfg)
install_data(packsiz, install_dir: bindir, install_mode: 'rwxr-xr-x')

packsiz_8 = configure_file(input:
                           'packsiz.8.in',
                           output: 'packsiz.8',
                           configuration: cfg)
# TODO: add support for targets as install_man() input
install_data(packsiz_8, install_dir: join_paths(get_option('mandir'), 'man8'))

install_data('README', 'COPYING', 'AUTHORS',
             install_dir: join_paths(get_option('datadir'), 'doc', 'packsiz'))
