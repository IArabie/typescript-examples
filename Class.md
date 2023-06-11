## Class

```ts
class Class {
    public token?: string;
    constructor(token?: string) {
        this.token = token;
    }

    setToken(token: string | undefined) {
        this.token = token;
        return this;
    }

    toJSON() {
        return { token: this.token };
    }
}

const Token = new Class()
    Token.setToken('API_KEY');
console.log(Token.toJSON()); 

/**
 * Result: { token: 'API_KEY' }
 */

```