---Title: GtGQLSnippet Page---#GtGQLSnippet Page- self storeString- (GtGQLSnippet new input: '{
	"ownername": "feenkcom",
	"reponame": "gtoolkit"
}'; operation: 'query Repository($ownername: String!, $reponame: String!) {
	repository(owner: $ownername, name: $reponame) {
		url
		description
	}
}'; yourself)