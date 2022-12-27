#!/usr/bin/env zsh

unset KEYNAME
unset MD
unset SHA
unset SUMS
echo -n "Enter name for new key: "
read KEYNAME
if [ -z $KEYNAME ]; then
  KEYNAME="newkey_$(date)"
fi
rm -rf ./keybase
COUNT="0"
until [ $COUNT = 33 ]; do
  dd if=/dev/random of=./keybase bs=1 count=333 &> /dev/null
  COUNT=$((COUNT+1))
  MD=$(md5sum ./keybase)
  MD=${MD:0:32}
  SHA=$(sha1sum ./keybase)
  SHA=${SHA:0:40}
  SUMS+=("$MD" "$SHA")
done
echo "${SUMS[@]}" > ./$KEYNAME
KEYFIN=$(cat ./$KEYNAME)
KEYFIN=${KEYFIN// /$RANDOM}
echo "$KEYFIN" > ./$KEYNAME
MDP=$(md5sum ./$KEYNAME)
MDP=${MDP:0:32}
SHAP=$(sha1sum ./$KEYNAME)
SHAP=${SHAP:0:40}
SUMSP+=("$MDP" "$SHAP")
SUMSP=${SUMSP[@]/ /l0l1m50rand0m}
echo $SUMSP > ./$KEYNAME-pub
PKEYFIN=$(cat ./$KEYNAME-pub)
PKEYFIN=${PKEYFIN// /l0l1m50rand0m}
echo "$PKEYFIN" > ./$KEYNAME-pub
rm -rf ./keybase
echo "$(tput setaf 3)-------------$(tput sgr 0)"
echo "$(tput setaf 3) private key $(tput sgr 0)"
echo "$(tput setaf 3)-------------$(tput sgr 0)"
echo " "
cat ./$KEYNAME
echo " "
echo "$(tput setaf 3)------------$(tput sgr 0)"
echo "$(tput setaf 3) public key $(tput sgr 0)"
echo "$(tput setaf 3)------------$(tput sgr 0)"
echo " "
cat ./$KEYNAME-pub
echo " "
echo "Generated $KEYNAME and $KEYNAME-pub"
