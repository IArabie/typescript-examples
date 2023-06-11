## MessageComponent
```ts
const Button = createMessageComponents({
    type: MessageComponentType.ACTION_ROW,
    components: [
        { type: MessageComponentType.BUTTON, style: ButtonStyle.BLURPLE, label: 'Button', custom_id: 'Button' },
        { type: MessageComponentType.BUTTON, style: ButtonStyle.LINK, label: 'Button', url: 'https://example.com' }
    ]
})

const Menu = createMessageComponents({
    type: MessageComponentType.ACTION_ROW,
    components: [{ 
        type: MessageComponentType.SELECT_MENU, 
        custom_id: 'SelectMenu',
        max_values: 5,
        min_values: 1,
        options: [
            { description: 'JavaScript Language', emoji: { name: 'js', id: '0', animated: false }, label: 'JavaScript', value: 'JavaScript' },
            { description: 'TypeScript Language', emoji: { name: 'ts', id: '0', animated: false }, label: 'TypeScript', value: 'TypeScript' },
            { description: 'CSS Language', emoji: { name: 'css', id: '0', animated: false }, label: 'CSS', value: 'CSS' },
            { description: 'HTML Language', emoji: { name: 'html', id: '0', animated: false }, label: 'HTML', value: 'HTML' },
            { description: 'C++ Language', emoji: { name: 'cpp', id: '0', animated: false }, label: 'C++', value: 'CPP' },
            { description: 'C Sharp Language', emoji: { name: 'csharp', id: '0', animated: false }, label: 'C Sharp', value: 'CSharp' },
            { description: 'Go Language', emoji: { name: 'go', id: '0', animated: false }, label: 'Go', value: 'go' },
            { description: 'Java Language', emoji: { name: 'java', id: '0', animated: false }, label: 'Java', value: 'Java' },
        ],
        placeholder: 'Select your Favourite Programming Languages?';
    }]
})

bot.createMessage(Message.channel.id, { components: [Button, Menu], content: 'TypeScript Examples' })
```

```ts
export enum ButtonStyle {
    BLURPLE = 1,
    GREY = 2,
    GREEN = 3,
    RED = 4,
    LINK = 5
}

export enum MessageComponentType {
    ACTION_ROW = 1,
    BUTTON = 2,
    SELECT_MENU = 3
}

export function createMessageComponents(options: MessageComponentsOptions) { return options };

export interface MessageComponentsOptions {
    type: MessageComponentType;
    components: ActionRowComponents[];
}

type ActionRowComponents = Button | SelectMenu;

type Button = InteractionButton | LinkButton;

interface BaseButton {
    disabled?: boolean;
    emoji?: Partial<DiscordEmoji>;
    label: string;
    type: MessageComponentType.BUTTON;
}

interface InteractionButton extends BaseButton {
    custom_id: string;
    style: Exclude<ButtonStyle, ButtonStyle.LINK>;
}

interface LinkButton extends BaseButton {
    style: ButtonStyle.LINK;
    url: string;
}

interface DiscordEmoji {
    id: string | null;
    name: string;
    animated?: boolean;
}

interface SelectMenu {
    custom_id: string;
    disabled?: boolean;
    max_values?: number;
    min_values?: number;
    options: SelectMenuOptions[];
    placeholder?: string;
    type: MessageComponentType.SELECT_MENU;
}

interface SelectMenuOptions {
    default?: boolean;
    description?: string;
    emoji?: Partial<DiscordEmoji>;
    label: string;
    value: string;
}
```