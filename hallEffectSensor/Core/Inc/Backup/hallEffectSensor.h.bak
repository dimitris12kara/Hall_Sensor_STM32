/*
 * hallEffectSensor.h
 *
 *  Created on: Dec 25, 2023
 *      Author: Karamanlis Dimitris
 */

#ifndef INC_HALLEFFECTSENSOR_H_
#define INC_HALLEFFECTSENSOR_H_

//Change it if different MCU
#include "stm32f4xx_hal.h"

#define PI 3.141592
#define RPM_CONVERSION 9.54

//Gear ratio of the wheel to engine/motor
#define GEAR_RATIO 6.3

//Base structure for all data for the Hall Effect Sensor
typedef struct hallEffectSensor{
	TIM_HandleTypeDef* counter;
	TIM_HandleTypeDef* timeOutTimer;
	uint32_t time_now;
	uint32_t time_before;
	uint16_t rpm;
	float vehicle_speed;
	float radius;
	float tuner;
	uint16_t clock_ratio;
	uint8_t isReady;
	uint16_t interruptPin;

}hallEffectSensor;

HAL_StatusTypeDef hallEffectInit(hallEffectSensor *_hf, float _radius, TIM_HandleTypeDef _counter,
		TIM_HandleTypeDef _timeOutTimer, float _tuner, uint16_t _interruptPin);

void hallEffectCalculator(hallEffectSensor *_hf);



#endif /* INC_HALLEFFECTSENSOR_H_ */
