# Maintainer: dgnet <dgnet@dgnet.com>
# Contributor: andriy <andriy@dgnet.cloud>
# https://wiki.archlinux.org/title/creating_packages
# https://wiki.archlinux.org/title/Python_package_guidelines

pkgname=PID1
pkgver=r8.601f58b
pkgrel=1
pkgdesc="The python program to manage DGnet_Dist_PIDX repositories throug the GitHub API"
arch=('any')
url="https://github.com/andriykutsevol/DGnet_Dist_PID1.git"
license=('')
# Note: Dependencies from setup.py must be defined in the depends array otherwise they will not be installed.
depends=("python-pygithub")
# makedepends=('git')
# checkdepends=('python-jaraco.envs' 'python-jaraco.path' 'python-mock' 'python-pip'
#               'python-pytest-fixture-config' 'python-pytest-flake8' 'python-pytest-virtualenv'
#               'python-wheel' 'python-paver' 'python-pytest-cov' 'python-sphinx')


source=("$pkgname::git+https://github.com/andriykutsevol/DGnet_Dist_PID1.git")

md5sums=('SKIP')

# With this function, commands that are used to prepare sources for building are run, 
# such as patching. This function runs right after package extraction, 
# before pkgver() and the build function. 
# If extraction is skipped (makepkg --noextract), then prepare() is not run.

prepare() {
	echo "start prepare()"
	echo $pkgdi
	echo "end prepare()"
}


# pkgver() runs after the sources are fetched, extracted and prepare() executed.
pkgver() {
        cd "$srcdir/${pkgname}"
        printf "r%s.%s" "$(git rev-list --count HEAD)" "$(git rev-parse --short HEAD)"
}


# The first step in the build() function is to change into the directory created by uncompressing the source tarball. 
# makepkg will change the current directory to $srcdir before executing the build() function. 
#build() {
#  cd "$srcdir/$pkgname"
#  python3 ../../setup.py build
#}

package() {
  mkdir -p $pkgdir/home/dgnet/dgnet_programs/PID1
  cd $pkgdir/home/dgnet/dgnet_programs/PID1
  python3 -m venv ./venv
  source ./venv/bin/activate
  pip install PyGithub
	
  cd "$srcdir/$pkgname"
  # cp -R ./* $pkgdir/home/dgnet/dgnet_programs/PID1
  # this will create an .egg file inside venv's site-packages
  python3 ../../setup.py install --root="$pkgdir/home/dgnet/dgnet_programs/PID1" --optimize=1 --skip-build
}



# git clone https://github.com/andriykutsevol/DGnet_Dist_PID1.git
# [dgnet@andriyarch PID1]$ pwd
# /home/dgnet/PID1

# makepkg --skipinteg --skipchecksums --skippgpcheck


# sudo pacman -U ./PID1-"tab key"
# source /home/dgnet/dgnet_programs/PG1/venv/bin/activate
# cd ~/ python3 -m PID1
# pacman -Qe	# List explictly-installed packages
# pacman -Ql PID1 # What files does this package have?
# sudo pacman -R PID1

# git clone https://github.com/andriykutsevol/DGnet_Dist_PID1.git
# Copy the setup.py in to the repos folder.
# python3 ./setup.py install --root="/home/dgnet/PID1_git/install" --optimize=1 --skip-build
# /home/dgnet/PID1_git/install/usr/lib/python3.10/site-packages/PID1-0.1-py3.10.egg-info





# [root@home]$ echo "/usr/local/lib/python2.7/site-packages/" > /opt/python2.7.2/lib/python2.7/site-packages/usrlocal.pth
# https://superuser.com/questions/247620/how-to-globally-modify-the-default-pythonpath-sys-path
# I'd like to summarize my findings about python's path modification. There are two ways to do it.

# .pth file
# PYTHONPATH

# Any .pth file which is found on the default path (see bellow) will get 
# its content included into sys.path. Format of said .pth file is simple: 
# one (folder) path per line. Surprisingly, 
# the paths can be absolute or relative to the .pth file.

# Default path is where the interpreter resides and 
# <some-prefix>/lib/python<version>/site-packages where <some-prefix> is usually /usr/.

# PYTHONPATH is environmental variable of your operating system. 
# On unix systems you list them by env. 
# Global modification of such variables is done through .sh scripts 
# inside /etc/profile.d/ folder as mentioned by @TestUser16418.



