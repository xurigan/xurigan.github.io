# git删除tag

## 删除所有本地tag

```ruby
git tag -d $(git tag -l)
```

## 获取远程tag

```ruby
git fetch
```

## 删除所有远程tag

```ruby
git push origin --delete $(git tag -l)
```

## 删除所有本地tag

```ruby
git tag -d $(git tag -l)
```

