---
	"ownername": "feenkcom",
	"reponame": "gtoolkit"
}'; operation: 'query Repository($ownername: String!, $reponame: String!) {
	repository(owner: $ownername, name: $reponame) {
		url
		description
	}
}'; yourself)