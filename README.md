
import { render , unmountComponentAtNode} from 'react-dom';
import { act} from 'react-dom/test-utils';
//import component for test 
import Hello from './Hello';
let container = null; // define container for render component

beforeEach(() => { // before start test
    container = document.createElemanr('div');
    document.body.appendChild(container);
});

afterEach(()=> { // after each  test
    unmountComponentAtNode(container);
    container.remove();
    container =null;
});

it('render without name a name', ()=> { // render component and test 
    act(()=> render(<Hello/> , container));
    expect(container.textContent).toBe('hey mahendra');
    act(()=> render(<Hello name ="hello"/> , container));
    expect(container.textContent).toBe('hello');
});

it("renders user data", async () => { /* Mock API test  */
    // mock data define
  const fakeUser = {
    name: "Joni Baez",
    age: "32",
    address: "123, Charming Avenue"
  };
  
    //mock API test 
    jest.spyOn(global, 'fetach').mockImplementation(()=> Promise.resolve({json: ()=> Promise.resolve(fakeUser)}))
});
