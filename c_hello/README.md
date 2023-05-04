


MT= multi thread多线程安全

=============================================
# simple-tss-rsa-lib
a simple sample for tss rsa lib usage...


1. install tss-rsa-lib in mac env..

2.
vim .zshrc or vim .bash_profile add....

export PATH="/opt/homebrew/opt/openssl@3/bin:$PATH"
export OPENSSL_ROOT_DIR="/opt/homebrew/opt/openssl@3"

=======================================================


simple-tss-ecd-lib
cmake .. -DOPENSSL_ROOT_DIR=/usr/local/include/openssl  -DENABLE_TESTS=ON




=======================================================