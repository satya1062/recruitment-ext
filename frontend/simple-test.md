//This is a Child component whic will show the Items in a List formate.

//You have to define super(props) inside constructor.Without super you can't access the props in side the state.

import React from 'react'

class SomeListComponent extends React.Component {
  constructor (props) {
	super(props); //without super you can't access the props in side the state.
    this.state = { items: props.items }
  }

  shouldComponentUpdate (nextProps) {
    return nextProps.items !== this.props.items //if the previous state items is not equal to the current state items,then render the component.
  }

  handleClick (index) {
    this.props.onClick(index) // this wiil call the onClick event which is define inside the parent component.Here you will get the Index of the every list element when you click on the list of element.
  }

  renderElement (item, index) {
    return <li onClick={() => this.handleClick(index)}>{item.text}</li>
  }

  render () {
    return (
      <ul style={{ backgroundColor: 'red', height: 100 }}>
        {this.state.items.map((item, i) => this.renderElement(item, i))}
      </ul>
    )
  }
}

export default SomeListComponent
