---
order: 0
title: Popover
---


````jsx
import { Popover, Button } from 'antd-mobile';
const Item = Popover.Item;

const App = React.createClass({
  getInitialState() {
    return {
      visible: false,
      visible1: false,
      selected: '',
    };
  },
  onSelect(opt) {
    this.setState({
      visible: false,
      selected: opt.props.value,
    });
  },
  handleVisibleChange(visible) {
    this.setState({
      visible,
    });
  },
  render() {
    let overlay = [1, 2, 3].map((i, index) => <Item key={index} value={`option ${i}`}>option {i}</Item>);
    overlay = overlay.concat([
      <Item key="4" value="disabled" disabled>disabled opt</Item>,
      <Item key="5" value="special" iconName="github">special opt</Item>,
      <Item key="6" value="button ct" iconName="github">
        <Button
          size="small"
          inline
          onClick={() => this.handleVisibleChange(false)}
        >
          关闭
        </Button>
      </Item>,
    ]);

    return (<div>
      <Popover
        visible={this.state.visible}
        overlay={overlay}
        popupAlign={{
          offset: [5, 14],
        }}
        onVisibleChange={this.handleVisibleChange}
        onSelect={this.onSelect}
      >
        <a href="#" style={{ float: 'right', marginRight: 100 }}>菜单</a>
      </Popover>
      {/* <p>选中了 {this.state.selected}</p> */}
      <div style={{ paddingTop: 140, paddingLeft: 130 }}>
        <Popover
          visible={this.state.visible1}
          overlay={[
            <Item key="0" value="0">添加朋友</Item>,
            <Item key="1" value="1">发起群聊</Item>,
            <Item key="2" value="2">扫一扫</Item>,
            <Item key="3" value="3">我的二维码</Item>,
          ]}
          popupAlign={{
            offset: [-5, -14],
          }}
          placement="topRight"
          onVisibleChange={v => this.setState({ visible1: v })}
        >
          <a href="#">菜单</a>
        </Popover>
      </div>
    </div>);
  },
});

ReactDOM.render(<App />, mountNode);
````
