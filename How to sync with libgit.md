---Title: How to sync with libgit---#How to sync with libgit- [[howto]] [[github]]- See [[AC]] [tip on slack](https://feenk.slack.com/archives/C3PU92BMW/p1652112449965829)- targetFolder := FileLocator imageDirectory / 'pharo-local' / 'analysis'.tergetFolder ensureCreateDirectory.- remoteUrl := 'git@github.com:polypoly-eu/polyPod.git'- cloneCommand := (IceGitClone new)	location: targetFolder / 'polyPod';	url: remoteUrl.cloneCommand execute- IceRepositoryCreator new
  remote: (IceGitRemote url: '<yoururl>');
  location: targetFolder; "from above"
  createRepository