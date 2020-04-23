# react-native-step-ui
A demo of simple react native step ui

Step.js

```
// @flow
import { Component } from 'react';
import * as React from 'react';
import { View, Text } from 'react-native';
import styles from './styles';

interface StepProps {
  itemList: any,
}
interface StepState {

}

export default class Step extends Component<StepProps, StepState> {

  getCircleContainerStyle(index: number) {
    const { itemList } = this.props;
    if (index === 0) {
      return styles.firstCircleContainer;
    } else if (index === itemList.length - 1) {
      return styles.lastCircleContainer;
    } else {
      return styles.circleContainer;
    }
  }

  getLabelContainerStyle(index: number) {
    const { itemList } = this.props;
    if (index === 0) {
      return styles.firstLabelContainer;
    } else if (index === itemList.length - 1) {
      return styles.lastLabelContainer;
    } else {
      return styles.labelContainer;
    }
  }

  getItemStyle(index: number) {
    const { itemList } = this.props;
    if (index === itemList.length - 1) {
      return styles.lastItem;
    } else {
      return styles.item;
    }
  }

  render() {
    const { itemList } = this.props;
    return (
      <View style={styles.container}>
        <View style={styles.step}>
          {
            itemList && itemList.map((item, index) => (
              <View style={this.getItemStyle(index)}>
                <View style={this.getCircleContainerStyle(index)}>
                  <View style={styles.circle} />
                </View>
                <View style={this.getLabelContainerStyle(index)}>
                  <Text style={styles.label}>{item}</Text>
                </View>
              </View>
            ))
          }
        </View>
      </View>
    )
  }
}
```

style.js
```
// @flow
import EStyleSheet from 'react-native-extended-stylesheet';

const spaceBetweenItems = 45;
const stepColor = '#999999';
const labelColor = '#333333';
const labelMarginLeft = 15;
const circleHeight = 9;
const circleOffset = -1 - (circleHeight/2);

export default EStyleSheet.create({

  container: {
    paddingLeft: 20,
    paddingTop: 20,
  },

  item: {
    borderLeftWidth: 1,
    borderColor: stepColor,
    borderStyle: 'solid',
    borderRadius: 0,
    flexWrap: 'nowrap',
    alignItems: 'flex-start',
    flexDirection: 'row',
    paddingBottom: spaceBetweenItems,
  },

  lastItem: {
    borderLeftWidth: 1,
    borderColor: stepColor,
    borderStyle: 'solid',
    borderRadius: 0,
    flexWrap: 'nowrap',
    alignItems: 'flex-start',
    flexDirection: 'row',
    marginBottom: spaceBetweenItems,
  },

  circleContainer: {
    minHeight: 20,
    height: '100%',
    flexWrap: 'nowrap',
    justifyContent: 'center',
    flexDirection: 'column',
  },

  circle: {
    borderRadius: circleHeight,
    backgroundColor: stepColor,
    height: circleHeight,
    width: circleHeight,
    marginLeft: circleOffset,
  },

  labelContainer: {
    minHeight: 20,
    flexWrap: 'nowrap',
    justifyContent: 'center',
    flexDirection: 'column',
    marginLeft: labelMarginLeft,
  },

  label: {
    overflow: 'hidden',
    marginLeft: labelMarginLeft,
    color: labelColor,
    fontFamily: 'SourceSansPro-Bold',
    fontSize: 14,
  },

  firstCircleContainer: {
    minHeight: 20,
    height: '100%',
    flexWrap: 'nowrap',
    justifyContent: 'flex-start',
    flexDirection: 'column',
  },

  firstLabelContainer: {
    minHeight: 20,
    flexWrap: 'nowrap',
    justifyContent: 'flex-start',
    flexDirection: 'column',
    marginLeft: labelMarginLeft,
    marginTop: -3,
  },

  lastCircleContainer: {
    minHeight: 20,
    height: '100%',
    flexWrap: 'nowrap',
    justifyContent: 'flex-end',
    flexDirection: 'column',
  },

  lastLabelContainer: {
    minHeight: 20,
    flexWrap: 'nowrap',
    justifyContent: 'flex-end',
    flexDirection: 'column',
    marginLeft: labelMarginLeft,
    marginBottom: -3,
  }

});
```
