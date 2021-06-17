```

import { render , unmountComponentAtNode} from 'react-dom';
import { act} from 'react-dom/test-utils';
//import component for test 
import Hello from './Hello';

// define container for render component
let container = null; 

 // before start test
beforeEach(() => {
    container = document.createElemanr('div');
    document.body.appendChild(container);
});

// after each  test
afterEach(()=> { 
    unmountComponentAtNode(container);
    container.remove();
    container =null;
});

// render component and test 
it('render without name a name', ()=> { 
    act(()=> render(<Hello/> , container));
    expect(container.textContent).toBe('hey mahendra');
    act(()=> render(<Hello name ="hello"/> , container));
    expect(container.textContent).toBe('hello');
});

### Mock API test 
it("renders user data", async () => { 
    // mock data define
  const fakeUser = {
    name: "Joni Baez",
    age: "32",
    address: "123, Charming Avenue"
  };
  
    //mock API test 
    jest.spyOn(global, 'fetach').mockImplementation(()=> Promise.resolve({json: ()=> Promise.resolve(fakeUser)}))
});

```
