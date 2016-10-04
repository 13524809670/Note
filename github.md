可创建 【README.md】 做笔记

        github 新建项目上传 
    echo "# abc" >> README.md
    git init
    git add .  
    git status
    git commit -m "first commit"
    git remote add origin git@github.com:13524809670/abc.git
    git push origin master
    
    项目内如有node_modules则不上传在根目录创建 .gitignore 文件，再在文件内 写上文件名 node_modules 或者 文件名  则不会上传


        github 修改/添加项目上传
    git pull === git pull origin master
    git add .  （可直接写多个文件名）
    git commit -m "修改"
    git push

        github 新建 pages 分支
    ls                      //打开目录
    cd fileName             //进入某项目
    git branch              //查看分支
    git branch gh-pages     //创建分支
    git branch
    git checkout gh-pages   //切换到gh-pages
    git push -u origin gh-pages //上传到分支

        github 分支 修改/添加项目上传
    git pull
    git add .  （可直接写多个文件名）
    git commit -m "修改"
    git push gh-pages

    分支便于工作的修补  更改 解决 Bug 等问题
        ls -al   //查看目录
        git checkout master  //切换到 master 主分支
        git merge gh-pages //把 gh-pages 合并到 master 分支



    github上传常见问题(1)
    $ git push -u origin master
    error: src refspec master does not match any.
    error: failed to push some refs to 'git@github.com:13524809670/My-Component.git'
    原因：引起该错误的原因是，目录中没有文件，空目录是不能提交上去的

    解决方法
    touch README
    git add README 
    git commit -m 'first commit'
    git push origin master


    github上传常见问题(2)
    error: failed to push some refs to 'git@github.com:13524809670/BW.git'
    原因：出现错误的主要原因是github中的README.md文件不在本地代码目录中

    解决方法
    git pull --rebase origin master
    git push -u origin master
