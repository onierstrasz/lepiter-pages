---
LeMockedSnippet is used for testing
The rest are not exemplified. Jenkins is particularly useful
we will play with LeDockerSnippet this week
the GitHub snippets were more for exploration
	"ownername": "feenkcom",
	"reponame": "gtoolkit"
}'; operation: 'query Repository($ownername: String!, $reponame: String!) {
	repository(owner: $ownername, name: $reponame) {
		url
		description
	}
}'; yourself)