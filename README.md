# org-clock-alarm

#### 介绍
为org-clock 添加提醒功能,目的有两个:

1. 记录工作时间,方便统计在每个工作项目上花的时间
2. 防止过渡劳累工作,周期性提醒休息

#### 功能
**org-clock-watch添加的功能有:**

1. 如果计算机没有idle, 并且没有设置计时提醒,则弹出提醒,并播放声音提醒添加计时提醒
2. 如果计算机idel超过一定时间,则停止提醒,直到计算机不idle
3. 如果超时则周期性提醒休息,并播放声音
4. 如果需要延时,点击相应按钮,启动延时计时

**org-clock 已有功能:**

1. 统计一段时间内每个任务所花费的时间
2. 计算机idle超过一段时间,互动式恢复计时,如减去idel时间,保留指定时间等等
3. 开启org-clock 在modeline显示任务功能,则可显示当前任务



#### 安装教程

1.  emacs 自行查找安装gitee包的方法,并安装org-clock-watch

2.  spacemacs

    1. 在your-layer中添加包 

       (org-clock-watch :location (recipe :fetcher git :url "git@gitee.com:zongtao_wang/org-clock-watch.git" :branch "master" :files (:defaults "resources")))

    2. 配置包

       ```
       (defun your-layer/init-org-clock-watch()
           (use-package org-clock-watch
               :defer t
               :init
               (run-with-timer 1 1 'org-clock-watcher)
           ))

       ```
    3. 在init file 的dotspacemacs-configuration-layers中添加 your-layer

     `(your-layer :variables org-clock-watch-work-plan-file-path "/file/path/to/your/work/plan/org/file")`

#### 使用说明

1.  设置工作计划目录

    `setq org-clock-watch-work-plan-file-path "/path/to/your/org/file"`

#### 哲学
简单的任务就让它保持简单

org-clock 非常强大,这个包只"监视"org-clock的状态,并发出提醒, 所以你可以使用org-clock的全部功能.
