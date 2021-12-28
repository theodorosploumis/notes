# Get Drupal production configuration

```bash
ORIGIN=master
CURRENTDATE=`date +"%Y-%m-%d-%H-%M"`
BRANCH=prod-"$CURRENTDATE"

git checkout -b $BRANCH
drush cex -y
git add config
git commit -m "Prod: get config $CURRENTDATE"
git push origin $BRANCH

git merge $BRANCH master

git pull origin master
git push origin master

git branch -D $BRANCH
git push origin :$BRANCH
```
