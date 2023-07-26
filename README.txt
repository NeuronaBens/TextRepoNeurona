import { LinearClient } from '@linear/sdk';

export async function POST(request) {
  try {
    const apiKey = 'YOUR_PERSONAL_API_KEY';
    const client = new LinearClient({
      apiKey: apiKey
    });

    const data = await request.json();

    // Extract the necessary data from the request body
    const { title, description, teamId } = data;

    // Create a new issue using the issueCreate mutation
    const createIssueInput = {
      title: title,
      description: description,
      teamId: teamId
    };

    const issueCreateResponse = await client.mutation.issueCreate({
      input: createIssueInput
    });

    // Get the newly created issue from the response
    const newIssue = issueCreateResponse?.issue;

    // Return the created issue as the response
    return new Response(JSON.stringify(newIssue), {
      headers: {
        'Content-Type': 'application/json'
      },
      status: 201 // 201 indicates the resource was successfully created
    });
  } catch (error) {
    console.error('Error creating the issue:', error.message);

    return new Response(JSON.stringify({ error: 'Failed to create the issue' }), {
      headers: {
        'Content-Type': 'application/json'
      },
      status: 500 // 500 indicates an internal server error
    });
  }
}
