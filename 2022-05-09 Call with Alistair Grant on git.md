---Title: 2022-05-09 Call with Alistair Grant on git---#2022-05-09 Call with Alistair Grant on git- [[meetings]]- Discussed with [[AG]] how to manage git branches.- See also: [[How to work with git branches]]- `git branch` shows your current branch- `git branch -a` shows all the branches and where you are- `git remote -v` shows your state with respect to the remote repo- `git log` shows your recent actions since you cloned (?)- There is no need to merge with the release branch.- Use branches especially when working on a repo with others to avoid conflicts.- Periodically push your changes to the main branch, but keep your own branch clean so you can recover and return to it.- #Fixing the disconnected state    - Have two copies of main — the one I;m working on and the remote one    - We created a recovery branch: `git checkout -b recover`    - `git fetch origin` — copies the latest changes    - `git branch -a` shows all the branches we have    - We deleted the main branch: `git branch -D main`    - Then we copied the latest main: `git checkout main`    - We cherry-picked what we wanted from the recovery branch:    - `git cherry-pick 478fc7dc2d018554a71b9c408dec47ca16579461` etc    - We could find what we wanted from `git log recover`    - Finally we pushed: `git push`    - and we fixed the image by doing a Repair (trashing local changes).    - 1	10:52	git status
     2	10:53	git checkout -b recover
     3	10:53	git log
     4	10:54	git fetch
     5	10:54	git fetch origin
     6	10:54	git log
     7	10:54	git pull
     8	10:55	git pull origin main
     9	10:55	git log
    10	10:56	git revert de57053ea80c118a485919aa46f4576ee3ff91ea
    11	10:56	git revert de57053ea80c118a485919aa46f4576ee3ff91ea --hard
    12	10:56	git revert --hard de57053ea80c118a485919aa46f4576ee3ff91ea
    13	10:57	git pull --force origin main
    14	10:57	git log
    15	10:58	git pull --rebase --force origin main
    16	10:59	git rebase --abort
    17	10:59	git status
    18	11:00	git branch -d main
    19	11:00	git branch -D main
    20	11:00	git checkout main
    21	11:00	git log
    22	11:03	git log recover
    23	11:03	git cherry-pick 478fc7dc2d018554a71b9c408dec47ca16579461
    24	11:04	git cherry-pick 0158cc8c5e07218b743996b31422c9cff8f8c7ba
    25	11:04	git cherry-pick 0158cc8c5e07218b743996b31422c9cff8f8c7ba
    26	11:05	git cherry-pick --abort
    27	11:05	git log
    28	11:06	git log recover
    29	11:06	h
    30	11:06	git cherry-pick f1e26beba15950594bd238eadbac730c3123d5a5
    31	11:06	git log
    32	11:07	git push
    33	11:07	git status
    34	11:09	h
    35	11:10	git branch -a
    36	11:16	h