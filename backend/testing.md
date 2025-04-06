# Test files

## Guidelines

- Make the Arrange, Act, and Assert parts of the test clearly visible.
- Use the [object mother pattern](https://jonasg.io/posts/object-mother/) when you need to create complex test data.
- Prefer state-based testing to behaviour-based testing (see [Mocks aren't Stubs by Martin Fowler](https://martinfowler.com/articles/mocksArentStubs.html) 
and [Fake it till you Mock it by Younes Jaaidi](https://cookbook.marmicode.io/angular/fake-it-till-you-mock-it)).
- Write explicit tests that describe real business scenario. 

Example of a test:

```typescript
describe('PostMessageUseCase', () => {
  let useCase: PostMessageUseCase;
  let threadRepository: ThreadsRepositoryFake;
  let llmFacade: LlmFacadeFake;
  
  beforeEach(() => {
    threadRepository = new ThreadsRepositoryFake();
    llmFacade = new LlmFacadeFake();
    useCase = new PostMessageUseCase(threadRepository, llmFacade);
  });
  
  it('adds a new message to the thread', async () => {
    const thread = ThreadMother.emptyThread('thread-id').build();
    threadRepository.save(thread);
    llmFacade.setAnswer('Good, thank you !');
    
    await useCase.postMessage({ threadId: 'thread-id', content: 'Hello, how are you?' });
    
    expect(threadRepository.get(thread.id)).getData().toMatchObject({
      messages: [
        { sender: 'user', content: 'Hello, how are you?' },
        { sender: 'assistant', content: 'Good, thank you !' },
      ],
    });
  })
})
```
